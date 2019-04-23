---
title: Toplu işlemler (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
ms.assetid: 962a49d1-cc11-4b96-bc7d-071dd6607d6c
ms.openlocfilehash: a9f74f025af6dfc5737ea9f4971f68c5ad913e8b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59133607"
---
# <a name="batching-operations-wcf-data-services"></a>Toplu işlemler (WCF Data Services)
[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] Destekler toplu işleme isteklerinin bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-bağlı hizmeti. Daha fazla bilgi için [OData: Toplu işleme](https://go.microsoft.com/fwlink/?LinkId=186075). İçinde [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], kullanan her işlem <xref:System.Data.Services.Client.DataServiceContext>Sorguyu yürüten veya veri hizmetine gönderilen ayrı bir istek sonuçlarında değişiklikleri kaydetmeden gibi. İşlem kümesi için mantıksal bir kapsam sürdürmek için operasyonel toplu açıkça tanımlayabilirsiniz. Bu, toplu işlemdeki tüm işlemleri tek bir HTTP isteği veri hizmetine gönderilen, server'ın atomik olarak işlemlerini sağlar ve veri hizmetine gidiş dönüş sayısını azaltan sağlar.  
  
## <a name="batching-query-operations"></a>Sorgu işlemleri toplu işleme  
 Tek bir toplu işlemde birden çok sorgu yürütmek için her sorgu toplu işlemde ayrı bir örneği oluşturmalısınız <xref:System.Data.Services.Client.DataServiceRequest%601> sınıfı. Bu şekilde bir sorgu isteği oluşturduğunuzda, sorgunun kendisi bir URI olarak tanımlanır ve kaynaklarını adreslemek için kuralları izler. Daha fazla bilgi için [veri hizmeti kaynaklarına erişme](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md). Toplu sorgu istekleri için veri gönderilir ne zaman hizmet <xref:System.Data.Services.Client.DataServiceContext.ExecuteBatch%2A> yöntemi sorgu isteği nesneleri içeren çağrılır. Bu yöntem döndürür bir <xref:System.Data.Services.Client.DataServiceResponse> bir koleksiyon nesne, <xref:System.Data.Services.Client.QueryOperationResponse%601> her sorgu toplu yanıtlar temsil eden nesneleri, her biri içeren sorgu veya hata bilgileri tarafından döndürülen nesneler topluluğudur. Toplu işteki herhangi bir tek sorgu işlemi başarısız olduğunda hata bilgileri döndürülür <xref:System.Data.Services.Client.QueryOperationResponse%601> başarısız olan işlem nesnesi ve kalan işlemleri hala çalıştırılır. Daha fazla bilgi için [nasıl yapılır: Bir toplu işte sorgular yürütme](../../../../docs/framework/data/wcf/how-to-execute-queries-in-a-batch-wcf-data-services.md).  
  
 Toplu sorgular ayrıca zaman uyumsuz olarak çalıştırılabilir. Daha fazla bilgi için [zaman uyumsuz işlemler](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md).  
  
## <a name="batching-the-savechanges-operation"></a>SaveChanges işlemi toplu işleme  
 Çağırdığınızda <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> yöntemi, parçaları olarak gönderilir, REST tabanlı işlemler çevrilmiş içerik istekleri için tüm değişiklikleri [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] hizmeti. Varsayılan olarak, bu değişiklikler tek bir istek iletisinde gönderilmez. Tüm değişiklikleri tek bir istekte gönderilmesini istemek için çağırmalısınız <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%28System.Data.Services.Client.SaveChangesOptions%29> yöntemi ve değeri içeren <xref:System.Data.Services.Client.SaveChangesOptions.Batch> içinde <xref:System.Data.Services.Client.SaveChangesOptions> yöntemine sağladığınız sabit listesi.  
  
 Zaman uyumsuz olarak ayrıca toplu değişiklikleri kaydedebilirsiniz. Daha fazla bilgi için [zaman uyumsuz işlemler](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetleri İstemci Kitaplığı](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
