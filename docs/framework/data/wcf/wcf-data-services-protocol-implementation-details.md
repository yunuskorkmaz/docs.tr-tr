---
title: "Protokol uygulama ayrıntılarını WCF Veri Hizmetleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 712d689b-fada-4cbb-bcdb-d65a3ef83b4c
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1f5f723ddf5c81550661c6b96de77b35984b1eeb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="wcf-data-services-protocol-implementation-details"></a>Protokol uygulama ayrıntılarını WCF Veri Hizmetleri
## <a name="odata-protocol-implementation-details"></a>OData Protokolü uygulama ayrıntıları  
 [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] Protokolü uygulayan bir veri hizmeti işlevler belirli minimum kümesi sağlaması gerekir. Bu işlevler "gerekir" ve "gerekir." açısından Protokolü belgelerinde açıklanan İsteğe bağlı diğer işlevleri bakımından "olabilir." açıklanır Bu konuda, şu anda tarafından uygulanmadı Bu isteğe bağlı işlevler açıklanmaktadır [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Daha fazla bilgi için bkz: [OData Protokolü belgeleri](http://go.microsoft.com/fwlink/?LinkID=184554).  
  
### <a name="support-for-the-format-query-option"></a>$Format sorgu seçeneği için destek  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Protokolünü destekleyen JavaScript gösterimi (JSON) hem Atom akışları ve [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] sağlar `$format` akış yanıt biçimi istemek bir istemci izin vermek için sistem sorgusu seçeneği. Bu sistem sorgusu seçeneği veri hizmeti tarafından destekleniyorsa, isteğin Accept üstbilgi değeri geçersiz kılmanız gerekir. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]hem JSON hem de Atom akışları döndürme destekler. Ancak, varsayılan uygulama desteklemediği `$format` sorgu seçeneği ve yanıt biçimi belirlemek için yalnızca Accept üstbilgisi değerini kullanır. Durumlar vardır, veri hizmeti desteklemek üzere gerektiğinde `$format` sorgu istemcileri Accept üstbilgisi zaman ayarlanamıyor gibi seçeneği. Bu senaryoları desteklemek için bu seçeneği URI işlemek için veri hizmetinizi genişletmeniz gerekir. Bu işlev yükleyerek veri hizmetinize ekleyebilirsiniz [JSONP ve URL denetimli biçimi desteklemek için ADO.NET Data Services](http://go.microsoft.com/fwlink/?LinkId=208228) örnek projeden MSDN kod Galerisi'nden web sitesi ve verilerin hizmet projenize ekleme. Bu örnek kaldırır `$format` sorgu seçeneği ve Accept üstbilgisi değişiklikleri `application/json`. Dahil ettiğinizde örnek proje ve ekleme `JSONPSupportBehaviorAttribute` verilerinizi hizmet sınıfı hizmet sağlayan `$format` sorgu seçeneği `$format=json`. Bu örnek projenin daha fazla özelleştirme ayrıca işlemek için gerekli olduğunu `$format=atom` veya diğer özel biçimler.  
  
## <a name="wcf-data-services-behaviors"></a>Davranışları WCF Veri Hizmetleri  
 Aşağıdaki [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] davranışları açıkça tanımlanmamış tarafından [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokolü:  
  
### <a name="default-sorting-behavior"></a>Varsayılan sıralama davranışı  
 Ne zaman veri hizmetine gönderilen bir sorgu isteği içeren bir `$top` veya `$skip` sistem sorgusu seçeneği ve içermemesi `$orderby` sistem sorgusu seçeneği, döndürülen akışa göre artan sırada anahtar özellikleri sıralandığı. Sıralama sonuçları doğru disk belleği emin olmak için gerekli olmasıdır. Bunu yapmak için veri hizmeti bir sıralama ifadesi sorguya ekler. Disk belleği sunucu tabanlı veri hizmeti etkin olduğunda bu davranış da oluşur. Daha fazla bilgi için bkz: [veri hizmeti yapılandırma](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md). Sıralama döndürülen akışa denetlemek için içermelidir `$orderby` URI sorgu.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Veri Hizmetlerini Tanımlama](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [WCF Veri Hizmetleri İstemci Kitaplığı](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
