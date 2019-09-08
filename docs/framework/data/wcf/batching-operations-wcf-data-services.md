---
title: Toplu işleme Işlemleri (WCF Veri Hizmetleri)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
ms.assetid: 962a49d1-cc11-4b96-bc7d-071dd6607d6c
ms.openlocfilehash: 2a642bdfd6a8891c54c01a07609760bede2f5d5d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780506"
---
# <a name="batching-operations-wcf-data-services"></a>Toplu işleme Işlemleri (WCF Veri Hizmetleri)
, [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] İstek temelli bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]hizmete yönelik isteklerin toplu işlemesini destekler. Daha fazla bilgi için bkz [. OData: Toplu Işleme](https://go.microsoft.com/fwlink/?LinkId=186075). ' [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]De, bir sorgu yürütme veya <xref:System.Data.Services.Client.DataServiceContext>değişiklikleri kaydetme gibi ' ı kullanan her işlem, veri hizmetine ayrı bir istek gönderilmesine neden olur. İşlem kümelerine yönelik bir mantıksal kapsamı sürdürmek için, işlem toplu işlerini açık bir şekilde tanımlayabilirsiniz. Bu, toplu işlemdeki tüm işlemlerin tek bir HTTP isteğindeki veri hizmetine gönderilmesini, sunucunun işlemleri otomatik olarak işlemesini ve veri hizmetine gidiş dönüş sayısını azaltmasını sağlar.  
  
## <a name="batching-query-operations"></a>Sorgu Işlemlerini toplu işleme  
 Tek bir toplu işte birden çok sorgu yürütmek için, her sorguyu toplu iş içinde <xref:System.Data.Services.Client.DataServiceRequest%601> sınıfın ayrı bir örneği olarak oluşturmanız gerekir. Bu şekilde bir sorgu isteği oluşturduğunuzda, sorgunun kendisi bir URI olarak tanımlanır ve kaynakları adresleme kurallarını izler. Daha fazla bilgi için bkz. [veri hizmeti kaynaklarına erişme](accessing-data-service-resources-wcf-data-services.md). Toplu sorgu istekleri, <xref:System.Data.Services.Client.DataServiceContext.ExecuteBatch%2A> Yöntem sorgu isteği nesnelerini içeren çağrıldığında veri hizmetine gönderilir. Bu yöntem, her <xref:System.Data.Services.Client.DataServiceResponse> biri sorgu veya hata bilgileri tarafından döndürülen <xref:System.Data.Services.Client.QueryOperationResponse%601> bir nesne koleksiyonu içeren, toplu iş içindeki tek sorgulara verilen yanıtları temsil eden nesne koleksiyonu olan bir nesnesi döndürür. Toplu işteki tek bir sorgu işlemi başarısız olduğunda, başarısız olan işlem için <xref:System.Data.Services.Client.QueryOperationResponse%601> nesnede hata bilgileri döndürülür ve kalan işlemler hala yürütülür. Daha fazla bilgi için [nasıl yapılır: Sorguları bir toplu Işte](how-to-execute-queries-in-a-batch-wcf-data-services.md)yürütün.  
  
 Toplu sorgular, zaman uyumsuz olarak da çalıştırılabilir. Daha fazla bilgi için bkz. [zaman uyumsuz işlemler](asynchronous-operations-wcf-data-services.md).  
  
## <a name="batching-the-savechanges-operation"></a>SaveChanges Işlemini toplu işleme  
 <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> Yöntemini çağırdığınızda, içeriğin izlediği tüm değişiklikler [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] hizmete istek olarak gönderilen REST tabanlı işlemlere çevrilir. Varsayılan olarak, bu değişiklikler tek bir istek iletisinde gönderilmez. Tüm değişikliklerin tek bir istekte gönderilmesini gerektirmek için, <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%28System.Data.Services.Client.SaveChangesOptions%29> yöntemini çağırmanız ve yöntemine sağladığınız <xref:System.Data.Services.Client.SaveChangesOptions> sabit listesine <xref:System.Data.Services.Client.SaveChangesOptions.Batch> bir değeri eklemeniz gerekir.  
  
 Ayrıca toplu değişiklikleri zaman uyumsuz olarak kaydedebilirsiniz. Daha fazla bilgi için bkz. [zaman uyumsuz işlemler](asynchronous-operations-wcf-data-services.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetleri İstemci Kitaplığı](wcf-data-services-client-library.md)
