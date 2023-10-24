

    //实现搜索订单账号来入住的功能I
        // $("#search").click(function () {
        //     if($("#orderid").val()==""||$("#orderid").val()==null){
        //         alert('参数为空');
        //         vm.isfail=true;
        //         vm.tip_message="参数为空"
        //         return ;
        //     }
        //     vm.query_param=$("#orderid").val()
        //     let d={"id":$("#orderid").val()};
        //    $.post("../Get/ComeOrderById",d,function (data,status) {
        //        if (status=="success"){
        //            orderdata=data;
        //            let ale=$("div.alert");
        //            if(orderdata.status!="success"){
        //                vm.isfail=true;
        //                vm.tip_message=data.list[0].no;
        //                alert("订单账号查找失败");
        //            }
        //            else{
        //                vm.isfail=false;
        //                vm.tip_message="订单账号查找成功";
        //                vm.table_data=orderdata.list;
        //            }
        //        }
        //        else
        //            alert("error");
        //    })
        // });

        // 初始化页面
        // $.get("../Get/ComeOrderBill",function (dat,status) {
        //     console.log(dat);
        //     let data=JSON.parse(dat);
        //     if (status=="success"){
        //         if(data.status=="success"){
        //             vm.table_data=data.list;
        //             console.log(vm.table_data);
        //         }
        //         else {
        //             vm.table_data=[];
        //             vm.tip_message="查询失败"
        //         }
        //     }else {
        //         vm.tip_message="网络错误："+status;
        //     }
        // })
    public OrderBill comeRomeByRoomId(String roomid) {
    
        List<OrderBill> list = orderBillMapper.getByRoomIdOnDate(roomid);
        OrderBill orderBill=null;
        for (int i = 0; i < list.size(); i++) {
            orderBill = list.get(i);
            if (orderBill.getComeTime() != null && !orderBill.getComeTime().equals(""))
                break;
        }
        return orderBill;
    }
    
    //根据房间号从orderbill里面找账单
    public OrderBill comeRomeByRoomId(String roomid) {
    
        List<OrderBill> list = orderBillMapper.getByRoomIdOnDate(roomid);
        OrderBill orderBill=null;
        for (int i = 0; i < list.size(); i++) {
            orderBill = list.get(i);
            if (orderBill.getComeTime() != null && !orderBill.getComeTime().equals(""))
                break;
        }
        return orderBill;
    }