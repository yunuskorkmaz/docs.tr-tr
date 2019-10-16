---
title: 'En İyi Uygulamalar: Aracılar'
ms.date: 03/30/2017
ms.assetid: 2d41b337-8132-4ac2-bea2-6e9ae2f00f8d
ms.openlocfilehash: a7c037b5942a404b1ff790638979a8e430394151
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320795"
---
# <a name="best-practices-intermediaries"></a>En İyi Uygulamalar: Aracılar
Aracı üzerindeki hizmet tarafı kanalların düzgün şekilde kapatıldığından emin olmak için aracıları çağırırken hataları doğru şekilde işlemek için dikkatli olunmalıdır.  
  
 Aşağıdaki senaryoyu göz önünde bulundurun. İstemci bir aracı için çağrı yapar ve ardından arka uç hizmeti çağırır.  Arka uç hizmeti bir hata sözleşmesi tanımlamıyor, bu nedenle bu hizmetten oluşturulan herhangi bir hata, türsüz bir hata olarak kabul edilir.  Arka uç hizmeti bir @no__t 0 oluşturur ve WCF hizmet tarafı kanalını doğru bir şekilde iptal eder. @No__t-0 ' ı, sonra da aracı için oluşturulan <xref:System.ServiceModel.FaultException> olarak yüzeyler. Aracı <xref:System.ApplicationException> ' i yeniden oluşturur. WCF bunu, ara sunucudan yazılı olmayan bir hata olarak yorumlar ve istemciye iletir. Hata alındıktan sonra, hem aracı hem de istemci istemci tarafı kanallarını hatası. Ara sunucunun hizmet tarafı kanalı açık kalır, çünkü WCF hata önemli olduğunu bilmez.  
  
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
