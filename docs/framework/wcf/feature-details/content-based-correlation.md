---
title: İçeriğe Dayalı Bağıntı
ms.date: 03/30/2017
ms.assetid: f46a2b68-8d24-4122-bbee-9573fc3f9fb4
ms.openlocfilehash: 48009420788b8678f842c4368926e04f8a745a52
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33494221"
---
# <a name="content-based-correlation"></a>İçeriğe Dayalı Bağıntı
İş akışı Hizmetleri istemcileri ve diğer hizmetleri ile iletişim kurarken, genellikle var. benzersiz bir ileti belirli bir örneği ile ilişkilendirir bazı veri alışverişi iletilerindeki İçeriğe dayalı bağıntı iletide, müşteri numarası veya sipariş kimliği iletileri yönlendirmek için uygun iş akışı örneği gibi bu verileri kullanır. Bu konuda, iş akışlarında içerik tabanlı bağıntı kullanımı açıklanmaktadır.  
  
## <a name="using-content-based-correlation"></a>İçeriğe dayalı bağıntı kullanma  
 İçeriğe dayalı bağıntı bir iş akışı hizmeti tek bir istemci tarafından erişilen birden çok yöntemi vardır ve veri alışverişi iletilerindeki parçası istenen örneğini tanımlar olmadığında kullanılır.  
  
> [!NOTE]
>  İçeriğe dayalı bağıntı, bağlama için desteklenen içerik exchange bağlamaları birini olmadığından bağlam bağıntı kullanılamaz yararlıdır. Bağlam bağıntı hakkında daha fazla bilgi için bkz: [bağlam değişimi](../../../../docs/framework/wcf/feature-details/context-exchange-correlation.md).  
  
 Bu iletişimde kullanılan her Mesajlaşma etkinlik örneğini benzersiz şekilde tanımlar iletide verilerin konumu belirtmeniz gerekir. Bu sağlayarak gerçekleştirilir bir <xref:System.ServiceModel.MessageQuerySet>, kullanarak bir <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> veya <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>, ileti parçanın veya örneğini benzersiz şekilde tanımlamak veri parçası için sorgular.  
  
> [!WARNING]
>  Örneği tanımlamak için kullanılan veri bir bağıntı anahtara karma haline getirilir. Bağıntı için kullanılan veri benzersizdir Aksi takdirde karma anahtarında çakışması ortaya ve iletileri misrouted neden olmak için dikkatli olunması gerekir. Örneğin, aynı ada sahip birden çok müşteri olabileceğinden yalnızca müşteri adına göre bir bağıntı bir çakışma neden olabilir. İki nokta üst üste (`:`) ileti sorgunun anahtar ve değer daha sonra karma dizesi oluşturmak için sınırlandırmak için zaten kullanılmakta olduğundan ileti ilişkilendirmek için kullanılan verileri bir parçası olarak kullanılmamalıdır.  
  
 Aşağıdaki örnekte, ilk <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> bir iş akışı hizmetinde döndürür bir `OrderId`, hangi ardından geçirilen istemci tarafından aşağıdaki çağrıda <xref:System.ServiceModel.Activities.Receive> iş akışı hizmeti etkinliğinde.  
  
 [!code-csharp[CFX_ContentCorrelation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_contentcorrelation/cs/program.cs#1)]  
  
 Önceki örnekte de görüldüğü tarafından başlatılan içerik tabanlı bir bağıntı <xref:System.ServiceModel.Activities.SendReply>. <xref:System.ServiceModel.MessageQuerySet> Bu hizmete sonraki ileti tanımlamak için kullanılan veri olduğunu belirtir `OrderId`.  
  
 [!code-csharp[CFX_ContentCorrelation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_contentcorrelation/cs/program.cs#2)]  
  
 <xref:System.ServiceModel.Activities.Receive> İzleyen etkinliği <xref:System.ServiceModel.Activities.SendReply> tarafından başlatılmış bağıntı akışında izleyen <xref:System.ServiceModel.Activities.SendReply>. Her iki etkinlikler aynı paylaşmak <xref:System.ServiceModel.Activities.CorrelationHandle>, ancak her biri kendi <xref:System.ServiceModel.MessageQuerySet> ve <xref:System.ServiceModel.XPathMessageQuery> tanımlayıcı verileri belirli iletideki nerede belirtir. Bağıntı başlatır etkinlik bu <xref:System.ServiceModel.MessageQuerySet> belirtilen <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> özelliği ve tüm aşağıdaki <xref:System.ServiceModel.Activities.Receive> etkinlikleri kullanılarak belirtilir <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> özelliği.  
  
 [!code-csharp[CFX_ContentCorrelation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_contentcorrelation/cs/program.cs#3)]  
  
 İçeriğe dayalı bağıntı herhangi bir ileti etkinliği tarafından başlatılabilir (<xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, <xref:System.ServiceModel.Activities.ReceiveReply>) ne zaman veri akışları bir ileti bir parçası olarak. Belirli veri parçası bir ileti bir parçası olarak akış değil sonra kullanarak açıkça başlatılabilir <xref:System.ServiceModel.Activities.InitializeCorrelation> etkinlik. Birden çok veri parçalarını iletinin benzersiz şekilde tanımlamak için gereken sonra birden çok sorgu eklenebilir <xref:System.ServiceModel.MessageQuerySet>. Bu örneklerde, bir <xref:System.ServiceModel.Activities.CorrelationHandle> açıkça her kullanarak etkinlikleri sağlanan `CorrelatesWith` veya `CorrelationHandle` olup olmadığını yalnızca bir bağıntı Bu örnekte olduğu gibi tüm iş akışı için gereken her şeyi burada karşılık gelen ancak özellikleri üzerinde `OrderId`, tarafından sağlanan örtük bağıntı tanıtıcısı Yönetimi <xref:System.ServiceModel.Activities.WorkflowServiceHost> yeterlidir.  
  
## <a name="using-the-initializecorrelation-activity"></a>InitializeCorrelation etkinliğini kullanma  
 Önceki örnekte, `OrderId` çağırana aktarılan <xref:System.ServiceModel.Activities.SendReply> etkinliği ve bu değer bağıntı burada başlatıldı. Aynı davranışı kullanarak gerçekleştirilebilir <xref:System.ServiceModel.Activities.InitializeCorrelation> etkinlik. <xref:System.ServiceModel.Activities.InitializeCorrelation> Etkinlik alır <xref:System.ServiceModel.Activities.CorrelationHandle> ve iletiyi doğru örneğini eşleştirmek için kullanılan verilerini temsil eden öğeleri sözlüğü. Kullanmak için <xref:System.ServiceModel.Activities.InitializeCorrelation> önceki örnekte, etkinlik kaldırmak <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> gelen <xref:System.ServiceModel.Activities.SendReply> etkinliği ve kullanarak bağıntı Initialize <xref:System.ServiceModel.Activities.InitializeCorrelation> etkinlik.  
  
 [!code-csharp[CFX_ContentCorrelation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_contentcorrelation/cs/program.cs#4)]  
  
 <xref:System.ServiceModel.Activities.InitializeCorrelation> Etkinliği kullanılır iş akışı içinde veri önce doldurulur tutun değişkenleri sonra <xref:System.ServiceModel.Activities.Receive> başlatılmış ile karşılık gelen etkinlik <xref:System.ServiceModel.Activities.CorrelationHandle>.  
  
 [!code-csharp[CFX_ContentCorrelation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_contentcorrelation/cs/program.cs#5)]  
  
## <a name="configuring-xpath-queries-using-the-workflow-designer"></a>XPath sorguları iş akışı Tasarımcısı'nı kullanarak yapılandırma  
 Önceki örneklerde, etkinlikler ve ileti sorgularda kullanılan XPath sorguları kodda belirtildi. İş Akışı Tasarımcısı'nda [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] de XPaths gelen oluşturma yeteneği sağlar `DataContract` türleri için içerik tabanlı bağıntı. Önceki örnekte yapılandırılmış ilk XPath için yapılandırılan <xref:System.ServiceModel.Activities.SendReply>.  
  
 [!code-csharp[CFX_ContentCorrelation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_contentcorrelation/cs/program.cs#2)]  
  
 İş Akışı Tasarımcısı'nda XPath Mesajlaşma etkinliği yapılandırmak için iş akışı Tasarımcısı'nda etkinliği seçin. Önceki örnekte olduğu gibi bağıntı etkinliğini başlatma için üç nokta düğmesini tıklatmak **CorrelationInitializers** özelliğinde **özellikleri** penceresi. Bu görüntüler **eklemek bağıntı başlatıcıları** iletişim penceresi. Bu iletişim kutusundan bağıntı türünü belirtin ve bağıntı için kullanılan içerik seçin. <xref:System.ServiceModel.Activities.CorrelationHandle> Değişkeni belirtilen **Başlatıcısı ekleme** gelen kutusunda bağıntı türü ve bağıntı için kullanılan veri seçildiğinde **XPath sorguları** iletişim kutusunun bölümü.  
  
 ![CorrelationInitializer iletişim](../../../../docs/framework/wcf/feature-details/media/correlationinitializerdlg.jpg "CorrelationInitializerDlg")  
  
 Önceki örnekte ikinci XPath sorgusu içinde yapılandırılan <xref:System.ServiceModel.Activities.Receive> etkinlik.  
  
 [!code-csharp[CFX_ContentCorrelation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_contentcorrelation/cs/program.cs#3)]  
  
 Bağıntı Başlatmıyor Mesajlaşma bir etkinliği XPath sorgusunu yapılandırmak için iş akışı Tasarımcısı'nda etkinliği seçin ve ardından için üç nokta düğmesini tıklatın **CorrelatesOn** özelliğinde  **Özellikler** penceresi. Bu görüntüler **CorrelatesOn tanımı** iletişim penceresi.  
  
 ![CorrelatesOn tanımı](../../../../docs/framework/wcf/feature-details/media/correlatesondialog.jpg "CorrelatesOnDialog")  
  
 Bu iletişim kutusundan belirttiğiniz <xref:System.ServiceModel.Activities.CorrelationHandle> ve öğeleri seçin **XPath sorguları** XPath sorgusu oluşturmak için liste.
