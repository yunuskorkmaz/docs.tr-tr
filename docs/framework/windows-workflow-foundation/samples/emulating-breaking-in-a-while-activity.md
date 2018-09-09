---
title: Bir süredir kesme öykünme etkinliği
ms.date: 03/30/2017
ms.assetid: ddff715d-d623-4b54-b841-60bacbc3ca21
ms.openlocfilehash: 4938e07364609520f6528688877bce112be26d3f
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44253305"
---
# <a name="emulating-breaking-in-a-while-activity"></a>Bir süredir kesme öykünme etkinliği
Bu örnek şu etkinlikler döngü mekanizması bölme gösterir: <xref:System.Activities.Statements.DoWhile>, <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.While>, ve <xref:System.Activities.Statements.ParallelForEach%601>.  
  
 Windows Workflow Foundation (WF) bu döngüler yürütmeyi kesmek için herhangi bir etkinliği içermediğinden, bu yararlıdır.  
  
## <a name="scenario"></a>Senaryo  
 Örnek olan satıcıların listesini ilk güvenilir satıcıdan bulur (örneklerini `Vendor` sınıfı). Her satıcının bulunan bir `ID`, `Name` ve satıcı nasıl güvenilir ise belirleyen bir sayısal güvenilirlik değer. Örnek olarak adlandırılan özel bir etkinlik oluşturur `FindReliableVendor` iki giriş parametresi (Satıcılar ve en düşük güvenilirlik değeri bir liste) alan ve sağlanan ölçütlerle eşleşen listedeki ilk satıcısına döndürür.  
  
## <a name="breaking-a-loop"></a>Bir döngü sonu  
 Windows Workflow Foundation (WF), bir döngüyü kesmek için bir etkinlik içermiyor. Kod örneği kullanarak bir döngü bozucu gerçekleştirir bir <xref:System.Activities.Statements.If> etkinliği ve çeşitli değişkenleri. Örnekte, <xref:System.Activities.Statements.While> etkinlik bozuk bir kez `reliableVendor` değişkenine bir değerin atandığı dışında `null`.  
  
 Aşağıdaki kod örneğinde nasıl örnek bir süre sonu gösterir döngü.  
  
```csharp  
// Iterates while the "i" variable is lower than the size of the list   
// and any reliable Vendor is found.        
new While(env => i.Get(env) < this.Vendors.Get(env).Count && reliableVendor.Get(env) == null)  
{  
    DisplayName = "Main loop. Breaks when a reliable vendor is found",  
    Body = new Sequence  
    {                              
        Activities =  
        {  
            // This is the if used for setting the value of the break value…  
            new If  
            {  
                DisplayName = "Check for a reliable vendor",  
  
                //  If a vendor satisfies the reliability level…  
                Condition = new InArgument<bool>(env =>   
                           this.Vendors.Get(env)[i.Get(env)].Reliability >   
                           this.MinimumReliability.Get(env)),  
  
                // then assign that vendor to the reliable vendor variable and   
                // the while condition becomes false (exit the loop).  
                Then = new Assign<Vendor>  
                {  
                    To = reliableVendor,  
                    Value = new InArgument<Vendor>(env =>   
                                  this.Vendors.Get(env)[i.Get(env)])  
                }  
            },  
  
            // Increment the iteration variable.   
            new Assign<int>  
            {  
                DisplayName = "Increment iteration variable",  
                To = i,  
                Value = new InArgument<int>(env => i.Get(env) + 1)  
            }   
        }  
    }  
}  
```  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], EmulatingBreakInWhile.sln çözüm dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
3.  Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\EmulatingBreakInWhile`