---
title: "WCF Veri Hizmetleri İstemci Kitaplığı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, client library
- DataServiceQuery class, about DataServiceQuery class
- DataServiceContext class, about DataServiceContext class
ms.assetid: 21075e50-8917-413e-a8ea-35a0f6e65aa5
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1e321200ce4b3582d154c5a188584c9e0b12c10d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="wcf-data-services-client-library"></a>WCF Veri Hizmetleri İstemci Kitaplığı
Herhangi bir uygulama ile etkileşim kurabilen bir [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]-bir HTTP isteği ve işlem gönderirseniz, veri hizmeti temel [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akış veri hizmeti döndürür. Bu birlikte çalışabilirlik erişmenizi sağlayan [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-geniş bir aralık, Web özellikli uygulamalar Hizmetleri'nden tabanlı. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]daha zengin bir programlama deneyimi, kullandığında sağlayan istemci kitaplıklarını içerir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akışları .NET Framework veya Silverlight tabanlı uygulamalar.  
  
 İki ana sınıflardır istemci kitaplığının <xref:System.Data.Services.Client.DataServiceContext> sınıfı ve <xref:System.Data.Services.Client.DataServiceQuery%601> sınıfı. <xref:System.Data.Services.Client.DataServiceContext> Sınıfı karşı belirtilen veri hizmeti desteklenen işlemler yalıtır. Ancak [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Hizmetleri durum bilgisiz, içeriği değil. Bu nedenle, kullanabileceğiniz <xref:System.Data.Services.Client.DataServiceContext> değişiklik yönetimi gibi özellikleri desteklemek için veri hizmeti ile etkileşim arasında istemci durumunu korumak üzere sınıfı. Bu sınıf ayrıca kimlikleri yöneten ve değişiklikleri izler. <xref:System.Data.Services.Client.DataServiceQuery%601> Sınıfı, bir sorgu belirli varlık kümesini temsil eder.  
  
 Bu bölümde, istemci kitaplıkları erişme ve verileri bir .NET Framework istemci uygulamasından değiştirmek için nasıl kullanılacağı açıklanmaktadır. Nasıl kullanılacağı hakkında daha fazla bilgi için [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Silverlight tabanlı bir uygulama ile istemci kitaplığı bkz [WCF Veri Hizmetleri (Silverlight)](http://go.microsoft.com/fwlink/?LinkId=186016). Diğer istemci kitaplıkları kullanılabilir tüketen sağlayan bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] diğer tür uygulamaların akışı. Daha fazla bilgi için bkz: [OData SDK](http://go.microsoft.com/fwlink/?LinkID=185796).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Veri Hizmeti istemci kitaplığı oluşturma](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)  
 Bir istemci kitaplığı ve temel alan istemci veri hizmeti sınıfları oluşturmayı açıklar [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akışları.  
  
 [Veri Hizmeti sorgulama](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)  
 .NET Framework tabanlı bir uygulama veri hizmetinden istemci kitaplıkları kullanarak sorgulama açıklar.  
  
 [İçerik yükleme ertelenmiş](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)  
 İlk sorguyu yanıta dahil edilmeyen ek içerik yüklemek açıklar.  
  
 [Veri Hizmeti güncelleştirme](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md)  
 Oluşturmak, değiştirmek ve istemci kitaplıkları kullanarak varlıkları ve ilişkileri silmek açıklar.  
  
 [Zaman uyumsuz işlemler](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md)  
 Veri Hizmeti ile bir zaman uyumsuz olarak çalışmak için istemci kitaplıkları tarafından sağlanan özellikleri açıklar.  
  
 [Toplu işlem](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md)  
 Birden çok istek ile tek bir toplu veri hizmeti istemci kitaplıkları kullanarak nasıl gönderileceğini açıklar.  
  
 [Denetimlere veri bağlama](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md)  
 Denetimlere bağlama açıklar bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] bir veri hizmeti tarafından döndürülen akış.  
  
 [Arama hizmeti işlemleri](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md)  
 İstemci Kitaplığı hizmet işlemlerini çağırma için nasıl kullanılacağını açıklar.  
  
 [Veri Hizmeti içeriği yönetme](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md)  
 İstemci Kitaplığı davranışını yönetmek için seçenekleri açıklar.  
  
 [İkili verileri ile çalışma](../../../../docs/framework/data/wcf/working-with-binary-data-wcf-data-services.md)  
 Erişim ve bir veri akışı olarak veri hizmeti tarafından döndürülen ikili verileri değiştirmek açıklar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF veri hizmetleri tanımlama](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [Başlarken](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)
