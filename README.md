# VR-Controller
摄像的旋转的控制

Vector3 mouseLastPosition = new Vector3(-1, -1, -1);
//控制开发环境中通过鼠标上下左右查看周围环境
        if (mouseLastPosition.x == -1)
        {
			mouseLastPosition = Input.mousePosition;	//初始化参数，以保证第一次启动的时候镜头不乱动 Vector3 mouseLastPosition = new Vector3(-1, -1, -1);
        }
        if (Input.mousePosition.x != mouseLastPosition.x || Input.mousePosition.y != mouseLastPosition.y)
        {
            float cx = Input.mousePosition.x - mouseLastPosition.x;
            float cy = Input.mousePosition.y - mouseLastPosition.y;
            if (Math.Abs(cx) > Math.Abs(cy))
            {
                //X轴移动的更多，视为水平方向旋转 transform.Rotate (Vector3.up * Time.deltaTime*10);
                cameraTrans.Rotate(Vector3.up * Time.deltaTime * 6 * cx);
            }
            else
            {
                //Y轴移动量更大，视为垂直方向旋转
                cameraTrans.Rotate(Vector3.left * Time.deltaTime * 6 * cy);
            }
            mouseLastPosition = Input.mousePosition;
        }
