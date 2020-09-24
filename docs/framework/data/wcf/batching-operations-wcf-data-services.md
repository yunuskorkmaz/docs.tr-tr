---
title: Toplu işleme Işlemleri (WCF Veri Hizmetleri)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
ms.assetid: 962a49d1-cc11-4b96-bc7d-071dd6607d6c
ms.openlocfilehash: 95524c1397172e645d682a6ef3f03b17bb3a639d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166072"
---
# <a name="batching-operations-wcf-data-services"></a>Toplu işleme Işlemleri (WCF Veri Hizmetleri)

Açık Veri Protokolü (OData), isteklerin bir OData tabanlı hizmete toplu işlem işlemesini destekler. Daha fazla bilgi için bkz. [OData: Batch işleme](https://www.odata.org/documentation/odata-version-2-0/batch-processing/). WCF Veri Hizmetleri, bir sorgu yürütme veya değişiklikleri kaydetme gibi ' ı kullanan her işlem, <xref:System.Data.Services.Client.DataServiceContext> veri hizmetine ayrı bir istek gönderilmesine neden olur. İşlem kümelerine yönelik bir mantıksal kapsamı sürdürmek için, işlem toplu işlerini açık bir şekilde tanımlayabilirsiniz. Bu, toplu işlemdeki tüm işlemlerin tek bir HTTP isteğindeki veri hizmetine gönderilmesini, sunucunun işlemleri otomatik olarak işlemesini ve veri hizmetine gidiş dönüş sayısını azaltmasını sağlar.  
  
## <a name="batching-query-operations"></a>Sorgu Işlemlerini toplu işleme  

 Tek bir toplu işte birden çok sorgu yürütmek için, her sorguyu toplu iş içinde sınıfın ayrı bir örneği olarak oluşturmanız gerekir <xref:System.Data.Services.Client.DataServiceRequest%601> . Bu şekilde bir sorgu isteği oluşturduğunuzda, sorgunun kendisi bir URI olarak tanımlanır ve kaynakları adresleme kurallarını izler. Daha fazla bilgi için bkz. [veri hizmeti kaynaklarına erişme](accessing-data-service-resources-wcf-data-services.md). Toplu sorgu istekleri, <xref:System.Data.Services.Client.DataServiceContext.ExecuteBatch%2A> Yöntem sorgu isteği nesnelerini içeren çağrıldığında veri hizmetine gönderilir. Bu yöntem, <xref:System.Data.Services.Client.DataServiceResponse> <xref:System.Data.Services.Client.QueryOperationResponse%601> her biri sorgu veya hata bilgileri tarafından döndürülen bir nesne koleksiyonu içeren, toplu iş içindeki tek sorgulara verilen yanıtları temsil eden nesne koleksiyonu olan bir nesnesi döndürür. Toplu işteki tek bir sorgu işlemi başarısız olduğunda, <xref:System.Data.Services.Client.QueryOperationResponse%601> başarısız olan işlem için nesnede hata bilgileri döndürülür ve kalan işlemler hala yürütülür. Daha fazla bilgi için bkz. [nasıl yapılır: bir toplu Işte sorguları yürütme](how-to-execute-queries-in-a-batch-wcf-data-services.md).  
  
 Toplu sorgular, zaman uyumsuz olarak da çalıştırılabilir. Daha fazla bilgi için bkz. [zaman uyumsuz işlemler](asynchronous-operations-wcf-data-services.md).  
  
## <a name="batching-the-savechanges-operation"></a>SaveChanges Işlemini toplu işleme  

 <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A>Yöntemini çağırdığınızda, içeriğin izlediği tüm değişiklikler OData hizmetine istek olarak GÖNDERILEN REST tabanlı işlemlere çevrilir. Varsayılan olarak, bu değişiklikler tek bir istek iletisinde gönderilmez. Tüm değişikliklerin tek bir istekte gönderilmesini gerektirmek için, <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%28System.Data.Services.Client.SaveChangesOptions%29> yöntemini çağırmanız ve <xref:System.Data.Services.Client.SaveChangesOptions.Batch> yöntemine sağladığınız sabit listesine bir değeri eklemeniz gerekir <xref:System.Data.Services.Client.SaveChangesOptions> .  
  
 Ayrıca toplu değişiklikleri zaman uyumsuz olarak kaydedebilirsiniz. Daha fazla bilgi için bkz. [zaman uyumsuz işlemler](asynchronous-operations-wcf-data-services.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetleri İstemci Kitaplığı](wcf-data-services-client-library.md)
