---
title: "Özel Etkinlik bir aralık değerleri anahtara"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 441e0a17-421f-430c-ba97-59e4cc6c88e3
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ff6a55157e886b54d631d1ca5d2598785de7608d
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2017
---
# <a name="custom-activity-to-switch-on-a-range-of-values"></a>Özel Etkinlik bir aralık değerleri anahtara
Bu örnek kullanımını genişleten bir özel etkinlik oluşturmak nasıl gösteren bir <xref:System.Activities.Statements.Switch%601>. Geleneksel <xref:System.Activities.Statements.Switch%601> deyimi sağlar geçiş dayalı tek bir değer. Ancak, bir etkinlik burada geçmelidir senaryolarını değerleri aralığı alarak iş vardır. Örneğin, bir etkinlik bağlı anahtarlı değeri 1 ile 5 arasında olduğunda bir eylem, değer 6 ile 10 arasında olduğunda başka bir eylem ve diğer tüm değerler için varsayılan eylem yürütebilir. Bu özel etkinlik tam olarak bu senaryo sağlar.  
  
## <a name="the-switchrange-activity"></a>SwitchRange etkinliği  
 `SwitchRange` Etkinlik zamanlar alt etkinlik, ifadesinin sonucu değer bir aralık içinde dahil edildiğinde, `Cases`.  
  
 Aşağıdaki kod örneğinde anahtarları değerleri aralığı dayalı özel bir etkinliktir.  
  
```csharp  
public sealed class SwitchRange<T> : NativeActivity where T : IComparable  
{  
   [RequiredArgument]  
   [DefaultValue(null)]  
   public InArgument<T> Expression { get; set; }  
  
   public IList<CaseRange<T>> Cases  
  
   [DefaultValue(null)]  
   public Activity Default { get; set; }}  
}  
```  
  
|Özellik|Açıklama|  
|-|-|  
|İfade|Bu hesaplanan ve durumları listesinde aralıkları karşı karşılaştırıldığında ifadesidir. T türünde ifade sonucu|  
|Durumları|Her durumda, bir aralığı (başlangıç ve bitiş) ve bir etkinlik (gövde) oluşur. İfade değerlendirilir ve karşı aralıkları karşılaştırılır. İfadenin sonucu örneklerinin bir aralık içinde ise, karşılık gelen etkinlik yürütülür.|  
|Varsayılan|Hiçbir durumda eşleştiğinde çalıştırılan etkinliği. Ayarlandığında `null`, hiçbir işlem yapılmadı.|  
  
## <a name="caserange-class"></a>CaseRange sınıfı  
 `CaseRange` Sınıfı temsil eden bir aralıkta bir `SwitchRange` etkinlik. Her örneğinin `CaseRange` bir aralık içerdiği (oluşan bir `From` ve `To`) ve bir `Body` , zamanlanan etkinlik ifade `SwitchRange` aralık içinde değerlendirilir.  
  
 Aşağıdaki kod örneği için tanım `CaseRange` sınıfı.  
  
```  
public class CaseRange<T> where T : IComparable  
{  
    public T From { get; set; }  
  
    public T To { get; set; }  
  
    public Activity Action { get; set; }  
}  
```  
  
> [!NOTE]
>  Hem `SwitchRange` ve `CaseRange` örnekte tanımlanan sınıflar sınıflardır uygulayan herhangi bir türü ile çalışabilirsiniz genel `IComparable`gibi <xref:System.Activities.Statements.Switch%601> sınıfı.  
  
## <a name="sample-usage"></a>Örnek Kullanım  
 Aşağıdaki kod örneğinde nasıl kullanılacağı ortaya `SwitchRange` etkinlik.  
  
```csharp  
Activity SwitchRange = new SwitchRange<int>  
{  
    Expression = new InArgument<int>(value),  
    Cases =   
    {  
        new CaseRange<int>                      
        {  
            From = 1,  
            To = 5,  
            Action = new WriteLine  
            {  
                Text = "Case 1-5 selected",  
            }  
        },  
        new CaseRange<int>  
        {  
            From = 6,  
            To = 10,  
            Action = new WriteLine  
            {  
                Text = "Case 6-10 selected",  
            }  
        }  
    },  
    Default = new WriteLine { Text = "Default Case selected" }  
};  
```  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], SwitchRange.sln çözüm dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
3.  Çözümü çalıştırmak için CTRL + F5 tuşuna basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SwitchRange`