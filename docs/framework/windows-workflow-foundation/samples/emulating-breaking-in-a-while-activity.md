---
title: Bir süre sonu öykünen etkinliği
ms.date: 03/30/2017
ms.assetid: ddff715d-d623-4b54-b841-60bacbc3ca21
ms.openlocfilehash: 37c64c2b8dc03d58f9c2802edef644fe4888e87d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="emulating-breaking-in-a-while-activity"></a>Bir süre sonu öykünen etkinliği
Bu örnek, aşağıdaki etkinliklerin döngü mekanizması ayırmak gösterilmiştir: <xref:System.Activities.Statements.DoWhile>, <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.While>, ve <xref:System.Activities.Statements.ParallelForEach%601>.  
  
 Windows Workflow Foundation (WF) bu döngüler yürütülmesi ayırmak için herhangi bir etkinlik içermediğinden bu yararlı olur.  
  
## <a name="scenario"></a>Senaryo  
 Örnek satıcılarının listesini ilk güvenilir satıcıdan bulur (örneklerini `Vendor` sınıfı). Her satıcının bulunan bir `ID`, `Name` ve nasıl güvenilir satıcı mi belirleyen sayısal güvenilirlik değer. Örnek olarak adlandırılan özel bir etkinlik oluşturur `FindReliableVendor` , iki giriş parametreleri (Satıcılar ve en düşük güvenilirlik değer listesi) alır ve sağlanan ölçütlerle eşleşen listedeki ilk satıcısına döndürür.  
  
## <a name="breaking-a-loop"></a>Döngü kesiliyor  
 Windows Workflow Foundation (WF) bir döngüsünü kesmek için bir etkinlik içermez. Kod örneği kullanarak bir döngü çiğnemekten gerçekleştirir bir <xref:System.Activities.Statements.If> etkinliği ve çeşitli değişkenler. Örnekte, <xref:System.Activities.Statements.While> etkinlik bozulur kez `reliableVendor` değişkeni atanan değer dışında `null`.  
  
 Aşağıdaki kod örneğinde nasıl örnek biraz keser gösterilmektedir döngü.  
  
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
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
3.  Çözümü çalıştırmak için CTRL + F5 tuşuna basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\EmulatingBreakInWhile`