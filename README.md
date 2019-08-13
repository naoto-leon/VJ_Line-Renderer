# VJ_Line-Renderer_2
use LineRenderer made VJ kit 

#### LineRenderer覚書き
![VJ_Line-Renderer_2_gif](https://user-images.githubusercontent.com/43961147/62940743-308f5f00-be0f-11e9-95e9-4ead1d11df7d.gif)
*** 

LineRendererと三角関数で作りました。


    using System.Collections;
    using System.Collections.Generic;
    using UnityEngine;
　
     public class vj13 : MonoBehaviour
　    {
       public float input { get; set; }

    public GameObject[] point;

    public GameObject obj;
    private LineRenderer lineRenderer;


    [SerializeField]
    float posposX;
    [SerializeField]
    float posposY;

    [SerializeField]
    float magivOne;

    [SerializeField]
    float magivTwo;

    // Start is called before the first frame update
    void Start()
    {
        lineRenderer = obj.GetComponent<LineRenderer>();
        //lineRenderer.SetWidth(.2f, .2f);
        lineRenderer.SetColors(Color.white, Color.white);

        point = new GameObject[transform.childCount];
    }

    // Update is called once per frame
    void Update()
    {
        float angleDiff = 360f / (float)point.Length;



        for (int i = 1; i < point.Length; i = i + 2)
        {
            float angle = (angleDiff * i) * Mathf.Deg2Rad;

            point[i] = transform.GetChild(i).gameObject;
            Vector3 Pos = point[i].transform.position;

            lineRenderer.SetPosition(i, Pos);


            Pos.x = posposX+((5f + (input * (i*magivOne))) * Mathf.Cos(angle));
            Pos.y = posposY+((5f + (input * (i*magivOne))) * Mathf.Sin(angle));


            point[i].transform.position = Pos;
        }

        for (int i = 0; i < point.Length; i = i + 2)
        {
            float angle = (angleDiff * i) * Mathf.Deg2Rad;

            point[i] = transform.GetChild(i).gameObject;
            Vector3 Pos = point[i].transform.position;

            lineRenderer.SetPosition(i, Pos);


            Pos.x = posposX+((5f - (input * (i*magivTwo))) * Mathf.Cos(angle));
            Pos.y = posposY+((5f - (input * (i*magivTwo))) * Mathf.Sin(angle));


            point[i].transform.position = Pos;
        }
    }
    }
