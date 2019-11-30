---
title: Toplu işleme Işlemleri (WCF Veri Hizmetleri)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
ms.assetid: 962a49d1-cc11-4b96-bc7d-071dd6607d6c
ms.openlocfilehash: 48c0a5f1573f64396971e1265dbf467300a98406
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569351"
---
# <a name="batching-operations-wcf-data-services"></a>Toplu işleme Işlemleri (WCF Veri Hizmetleri)
Açık Veri Protokolü (OData), isteklerin bir OData tabanlı hizmete toplu işlem işlemesini destekler. Daha fazla bilgi için bkz. [OData: Batch işleme](https://go.microsoft.com/fwlink/?LinkId=186075). WCF Veri Hizmetleri, bir sorgu yürütme veya değişiklikleri kaydetme gibi <xref:System.Data.Services.Client.DataServiceContext>kullanan her işlem, veri hizmetine ayrı bir istek gönderilmesine neden olur. İşlem kümelerine yönelik bir mantıksal kapsamı sürdürmek için, işlem toplu işlerini açık bir şekilde tanımlayabilirsiniz. Bu, toplu işlemdeki tüm işlemlerin tek bir HTTP isteğindeki veri hizmetine gönderilmesini, sunucunun işlemleri otomatik olarak işlemesini ve veri hizmetine gidiş dönüş sayısını azaltmasını sağlar.  
  
## <a name="batching-query-operations"></a>Sorgu Işlemlerini toplu işleme  
 Tek bir toplu işte birden çok sorgu yürütmek için, her sorguyu toplu işte <xref:System.Data.Services.Client.DataServiceRequest%601> sınıfının ayrı bir örneği olarak oluşturmanız gerekir. Bu şekilde bir sorgu isteği oluşturduğunuzda, sorgunun kendisi bir URI olarak tanımlanır ve kaynakları adresleme kurallarını izler. Daha fazla bilgi için bkz. [veri hizmeti kaynaklarına erişme](accessing-data-service-resources-wcf-data-services.md). Toplu sorgu istekleri, sorgu isteği nesnelerini içeren <xref:System.Data.Services.Client.DataServiceContext.ExecuteBatch%2A> yöntemi çağrıldığında veri hizmetine gönderilir. Bu yöntem, toplu işteki tek tek sorgulara olan yanıtları temsil eden bir <xref:System.Data.Services.Client.QueryOperationResponse%601> nesneleri olan bir <xref:System.Data.Services.Client.DataServiceResponse> nesnesi döndürür; her biri sorgu veya hata bilgileri tarafından döndürülen bir nesne koleksiyonu içerir. Toplu işteki tek bir sorgu işlemi başarısız olduğunda, başarısız olan işlem için <xref:System.Data.Services.Client.QueryOperationResponse%601> nesnesinde hata bilgileri döndürülür ve kalan işlemler hala yürütülür. Daha fazla bilgi için bkz. [nasıl yapılır: bir toplu Işte sorguları yürütme](how-to-execute-queries-in-a-batch-wcf-data-services.md).  
  
 Toplu sorgular, zaman uyumsuz olarak da çalıştırılabilir. Daha fazla bilgi için bkz. [zaman uyumsuz işlemler](asynchronous-operations-wcf-data-services.md).  
  
## <a name="batching-the-savechanges-operation"></a>SaveChanges Işlemini toplu işleme  
 <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> yöntemini çağırdığınızda, içeriğin izlediği tüm değişiklikler OData hizmetine istek olarak gönderilen REST tabanlı işlemlere çevrilir. Varsayılan olarak, bu değişiklikler tek bir istek iletisinde gönderilmez. Tüm değişikliklerin tek bir istekte gönderilmesini gerektirmek için, <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%28System.Data.Services.Client.SaveChangesOptions%29> yöntemini çağırmanız ve yönteme sağladığınız <xref:System.Data.Services.Client.SaveChangesOptions> numaralandırmasında <xref:System.Data.Services.Client.SaveChangesOptions.Batch> bir değeri eklemeniz gerekir.  
  
 Ayrıca toplu değişiklikleri zaman uyumsuz olarak kaydedebilirsiniz. Daha fazla bilgi için bkz. [zaman uyumsuz işlemler](asynchronous-operations-wcf-data-services.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetleri İstemci Kitaplığı](wcf-data-services-client-library.md)
