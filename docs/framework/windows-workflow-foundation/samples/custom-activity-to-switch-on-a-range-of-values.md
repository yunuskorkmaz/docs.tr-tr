---
title: Üzerinde bir değer aralığına geçmek için özel etkinlik
ms.date: 03/30/2017
ms.assetid: 441e0a17-421f-430c-ba97-59e4cc6c88e3
ms.openlocfilehash: cfaf4318b1557a9fc217de8254e164243ea54569
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44067006"
---
# <a name="custom-activity-to-switch-on-a-range-of-values"></a>Üzerinde bir değer aralığına geçmek için özel etkinlik
Bu örnek, kullanımını genişleten özel etkinlik oluşturma işlemini gösterir. bir <xref:System.Activities.Statements.Switch%601>. Geleneksel <xref:System.Activities.Statements.Switch%601> deyimi geçişi sırasında tek bir değer temel sağlar. Ancak, bir etkinlik burada geçmelidir senaryolarını değer aralığını alarak iş vardır. Örneğin, bir etkinlik, geçiş sırasında değeri 1 ile 5 arasında olduğunda bir eylem, değer 6 ile 10 arasında olduğunda başka bir eylem ve diğer tüm değerler için bir varsayılan eylem paralellikle çalışabilir. Bu özel etkinlik tam olarak bir senaryo sağlar.  
  
## <a name="the-switchrange-activity"></a>SwitchRange etkinliği  
 `SwitchRange` Etkinliği, birinin aralığında, ifadenin sonucu değerini eklendiğinde bir alt etkinlik zamanlar kendi `Cases`.  
  
 Aşağıdaki kod örneği, anahtarları değerleri aralığı alan özel bir etkinliktir.  
  
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
|İfade|İfade değerlendirilir ve çalışmaları listesinde aralıkları karşı karşılaştırıldığında budur. İfadenin sonucu t türüdür|  
|Durumları|Her durumda, bir aralığı (başlangıç ve bitiş) ve bir etkinlik (gövde) oluşur. İfade değerlendirilir ve aralıkları karşı karşılaştırılır. İfadenin sonucu aralığı durumlarından biri içinde ise, karşılık gelen etkinlik yürütülür.|  
|Varsayılan|Hiçbir durum eşleştiğinde çalıştırılan etkinlik. Ayarlandığında `null`, hiçbir işlem yapılmaz.|  
  
## <a name="caserange-class"></a>CaseRange sınıfı  
 `CaseRange` Sınıfı temsil eder bir aralıkta bir `SwitchRange` etkinlik. Her örneğini `CaseRange` bir aralık içerdiği (oluşan bir `From` ve `To`) ve bir `Body` , zamanlanmış etkinlik ifadesinde `SwitchRange` aralığında değerlendirilir.  
  
 Aşağıdaki kod örneği için tanımıdır `CaseRange` sınıfı.  
  
```  
public class CaseRange<T> where T : IComparable  
{  
    public T From { get; set; }  
  
    public T To { get; set; }  
  
    public Activity Action { get; set; }  
}  
```  
  
> [!NOTE]
>  Hem `SwitchRange` ve `CaseRange` örnekte tanımlanan sınıflar olan uygulayan herhangi bir tür ile çalışabilir Genel sınıflar `IComparable`gibi <xref:System.Activities.Statements.Switch%601> sınıfı.  
  
## <a name="sample-usage"></a>Örnek kullanımı  
 Aşağıdaki kod örneğinde nasıl kullanılacağını gösterir `SwitchRange` etkinlik.  
  
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
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
3.  Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SwitchRange`