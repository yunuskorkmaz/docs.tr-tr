---
title: "En İyi Uygulamalar: Aracılar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2d41b337-8132-4ac2-bea2-6e9ae2f00f8d
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bfedfbd0177018de4affce67f16ee5f713f7d5de
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
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
 [WCF hata işleme](../../../docs/framework/wcf/wcf-error-handling.md)  
 [Belirtme ve sözleşme ve hizmetlerde hataları işleme](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
