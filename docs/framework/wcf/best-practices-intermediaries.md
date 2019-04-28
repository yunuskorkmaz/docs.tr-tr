---
title: 'En İyi Yöntemler: Aracılar'
ms.date: 03/30/2017
ms.assetid: 2d41b337-8132-4ac2-bea2-6e9ae2f00f8d
ms.openlocfilehash: 0bd553486bfb89a0ec14c42a1bb7d2ed9c4c540d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61608911"
---
# <a name="best-practices-intermediaries"></a>En İyi Yöntemler: Aracılar
Doğru hizmet tarafı kanalları aracı düzgün şekilde kapatıldığından emin olmak için aracılar çağrılırken arızları dikkatli olunması gerekir.  
  
 Aşağıdaki senaryoyu göz önünde bulundurun. Bir istemci, daha sonra bir arka uç hizmeti çağıran bir aracı için bir çağrı yapar.  Bu hizmetten oluşan herhangi bir hataya türsüz bir hata kabul edilecek şekilde arka uç hizmeti hiç hata sözleşme tanımlar.  Arka uç hizmeti oluşturur bir <xref:System.ApplicationException> ve WCF hizmet tarafı kanal doğru durdurur. <xref:System.ApplicationException> Olarak ortaya çıkarır bir <xref:System.ServiceModel.FaultException> aracı için oluşturulur. Aracıyı yeniden harekete <xref:System.ApplicationException>. WCF Bu Aracı'ndan türsüz bir hata olarak yorumlar ve istemci açın iletir. Hata aldıktan sonra hem bir aracı hem de istemci, istemci tarafı kanalları hata. WCF hata önemli bilmediği Aracı'nın hizmet tarafı kanal ancak açık kalır.  
  
 Bu senaryoda en iyi uygulama, önemli bir hizmetten gelen hata ise ve bu nedenle aracı, hizmet tarafı kanal aşağıdaki kod parçacığında gösterildiği gibi hata algılamaktır.  
  
```csharp  
catch (Exception e)  
{  
    bool faulted = service.State == CommunicationState.Faulted;  
    service.Abort();  
    if (faulted)  
    {  
        throw new ApplicationException(e.Message);  
    }  
    else  
    {  
        throw;  
    }  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Hata İşleme](../../../docs/framework/wcf/wcf-error-handling.md)
- [Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
