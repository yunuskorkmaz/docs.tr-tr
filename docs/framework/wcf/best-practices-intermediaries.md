---
title: 'En İyi Uygulamalar: Aracılar'
ms.date: 03/30/2017
ms.assetid: 2d41b337-8132-4ac2-bea2-6e9ae2f00f8d
ms.openlocfilehash: d69baae9b4f5851f60d8d1336c40e0d18db8e77d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="best-practices-intermediaries"></a>En İyi Uygulamalar: Aracılar
Hizmet tarafı kanalları aracı üzerinde düzgün kapalı olduğundan emin olmak için aracılar çağrılırken doğru hataları işlemek için dikkatli olunması gerekir.  
  
 Aşağıdaki senaryoyu göz önünde bulundurun. Bir istemci bir arka uç hizmeti çağıran bir aracı için bir çağrı yapar.  Bu hizmetinden durum hataya türsüz bir hata kabul edilecek şekilde arka uç hizmetine hiçbir hatalı sözleşme tanımlar.  Arka uç hizmetine atar bir <xref:System.ApplicationException> ve WCF doğru hizmet tarafı kanal durdurur. <xref:System.ApplicationException> Olarak ortaya çıkarır bir <xref:System.ServiceModel.FaultException> aracı için oluşturulur. Aracıyı yeniden oluşturur <xref:System.ApplicationException>. WCF bu aracı gelen türsüz bir hata olarak yorumlar ve istemci açın iletir. Hataya alındıktan sonra hem bir aracı hem de istemci kendi istemci-tarafı kanalları hata. WCF hata önemli bilmiyor olduğundan Aracı'nın hizmet tarafı kanal ancak açık kalır.  
  
 En iyi uygulama olarak bu senaryoda hizmetinden gelen önemli bir hatadır ve bu nedenle aracı kendi hizmet tarafı kanal aşağıdaki kod parçacığında gösterildiği gibi hata algılamaktır.  
  
```csharp  
catch (Exception e)  
{  
    bool faulted = service.State == CommunicationState.Faulted;  
    service.Abort();  
    if (faulted)  
    {  
        throw new ApplicationException(e.Message);  
    }  
    Else  
    {  
        throw;  
    }  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Hata İşleme](../../../docs/framework/wcf/wcf-error-handling.md)  
 [Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
