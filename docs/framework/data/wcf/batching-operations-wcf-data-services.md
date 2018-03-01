---
title: "Toplu işlemler (WCF Veri Hizmetleri)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, client library
ms.assetid: 962a49d1-cc11-4b96-bc7d-071dd6607d6c
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 65bf6bfd0bd437848137506605a958f5f2e8d750
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="batching-operations-wcf-data-services"></a>Toplu işlemler (WCF Veri Hizmetleri)
[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] Destekler toplu işleme isteklerinin bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-hizmet tabanlı. Daha fazla bilgi için bkz: [OData: toplu işleme](http://go.microsoft.com/fwlink/?LinkId=186075). İçinde [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], kullanan her bir işlemin <xref:System.Data.Services.Client.DataServiceContext>bir sorgu yürütülürken veya değişiklikleri, veri hizmetine gönderilen ayrı bir istek sonuçlarında kaydetme gibi. İşlem kümesi için mantıksal bir kapsam korumak için açıkça işletimsel toplu tanımlayabilirsiniz. Bu toplu işlemdeki tüm işlemleri tek bir HTTP istek veri hizmeti gönderilir, server'ın otomatik olarak işlemlerini sağlar ve veri hizmetine gidiş dönüş sayısını azaltan sağlar.  
  
## <a name="batching-query-operations"></a>Sorgu işlemleri toplu işleme  
 Tek bir toplu işlemde birden çok sorgularını yürütmek için her sorgu toplu işlemde ayrı bir örneği oluşturmalısınız <xref:System.Data.Services.Client.DataServiceRequest%601> sınıfı. Bu şekilde bir sorgu isteği oluşturduğunuzda, sorgu bir URI olarak tanımlanır ve kaynakları adresleme kurallara uygun olmalıdır. Daha fazla bilgi için bkz: [veri hizmeti kaynaklar erişim](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md). Toplu sorgu istekleri gönderilen verileri ne zaman hizmet <xref:System.Data.Services.Client.DataServiceContext.ExecuteBatch%2A> yöntemi sorgu isteği nesneleri içeren çağrılır. Bu yöntem bir <xref:System.Data.Services.Client.DataServiceResponse> bir nesne, <xref:System.Data.Services.Client.QueryOperationResponse%601> toplu işlemdeki tek tek sorguların yanıtlarını temsil eden nesneler, her biri içeren sorgu veya hata bilgilerini tarafından döndürülen nesne topluluğudur. Toplu işteki herhangi bir tek sorgu işlem başarısız olduğunda hata bilgilerini döndürülür <xref:System.Data.Services.Client.QueryOperationResponse%601> için başarısız olan işlem nesnesi ve kalan işlemleri hala yürütülür. Daha fazla bilgi için bkz: [nasıl yapılır: bir toplu iş yürütme sorgularda](../../../../docs/framework/data/wcf/how-to-execute-queries-in-a-batch-wcf-data-services.md).  
  
 Toplu sorguları da zaman uyumsuz olarak çalıştırılabilir. Daha fazla bilgi için bkz: [zaman uyumsuz işlemleri](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md).  
  
## <a name="batching-the-savechanges-operation"></a>SaveChanges işlemi toplu işleme  
 Çağırdığınızda <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> yöntemi, parçaları olarak gönderilen REST tabanlı işlemlere çevrilen içerik istekleri için tüm değişiklikleri [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] hizmet. Varsayılan olarak, bu değişiklikleri tek istek iletisinde gönderilmez. Tüm değişiklikleri tek bir istekte gönderilmesini istemek için çağırmalısınız <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%28System.Data.Services.Client.SaveChangesOptions%29> yöntemi ve değeri içeren <xref:System.Data.Services.Client.SaveChangesOptions.Batch> içinde <xref:System.Data.Services.Client.SaveChangesOptions> yönteme sağladığınız numaralandırması.  
  
 Toplu değişiklikleri de zaman uyumsuz olarak kaydedebilirsiniz. Daha fazla bilgi için bkz: [zaman uyumsuz işlemleri](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Veri Hizmetleri İstemci Kitaplığı](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
