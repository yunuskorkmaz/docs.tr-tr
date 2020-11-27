---
title: 'En İyi Yöntemler: Aracılar'
ms.date: 03/30/2017
ms.assetid: 2d41b337-8132-4ac2-bea2-6e9ae2f00f8d
ms.openlocfilehash: 57be78681147dfc5bc37701a76c1347040f5da1f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96277900"
---
# <a name="best-practices-intermediaries"></a>En İyi Yöntemler: Aracılar

Aracı üzerindeki hizmet tarafı kanalların düzgün şekilde kapatıldığından emin olmak için aracıları çağırırken hataları doğru şekilde işlemek için dikkatli olunmalıdır.  
  
 Şu senaryoyu düşünün. İstemci bir aracı için çağrı yapar ve ardından arka uç hizmeti çağırır.  Arka uç hizmeti bir hata sözleşmesi tanımlamıyor, bu nedenle bu hizmetten oluşturulan herhangi bir hata, türsüz bir hata olarak kabul edilir.  Arka uç hizmeti bir <xref:System.ApplicationException> ve WCF 'yi, hizmet tarafı kanalını doğru bir şekilde iptal eder. <xref:System.ApplicationException>Sonra, aracı olarak oluşturulan yüzeyleri <xref:System.ServiceModel.FaultException> . Aracı yeniden oluşturur <xref:System.ApplicationException> . WCF bunu, ara sunucudan yazılı olmayan bir hata olarak yorumlar ve istemciye iletir. Hata alındıktan sonra, hem aracı hem de istemci istemci tarafı kanallarını hatası. Ara sunucunun hizmet tarafı kanalı açık kalır, çünkü WCF hata önemli olduğunu bilmez.  
  
 Bu senaryodaki en iyi yöntem, hizmetten gelen hatanın önemli olup olmadığını algılamadır ve bu durumda aracı aşağıdaki kod parçacığında gösterildiği gibi hizmet tarafı kanalını hatasına memelidir.  
  
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

- [WCF Hata İşleme](wcf-error-handling.md)
- [Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme](specifying-and-handling-faults-in-contracts-and-services.md)
