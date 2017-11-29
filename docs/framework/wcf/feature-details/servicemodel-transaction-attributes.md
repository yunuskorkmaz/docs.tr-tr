---
title: "ServiceModel İşlem Öznitelikleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: transactions [WCF], ServiceModel attributes
ms.assetid: 1e0d2436-6ae5-439b-9765-a448d6f60000
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4857c6e9f77e8cf201c47814405e4db9f08ae2d8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="servicemodel-transaction-attributes"></a>ServiceModel İşlem Öznitelikleri
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]üç standardını temel özellikleri sağlar <xref:System.ServiceModel> işlemleri için davranışını yapılandırmanızı sağlayan öznitelikler bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmeti:  
  
-   <xref:System.ServiceModel.TransactionFlowAttribute>  
  
-   <xref:System.ServiceModel.ServiceBehaviorAttribute>  
  
-   <xref:System.ServiceModel.OperationBehaviorAttribute>  
  
## <a name="transactionflowattribute"></a>TransactionFlowAttribute  
 <xref:System.ServiceModel.TransactionFlowAttribute> Özniteliği, bir istemciden gelen işlemler kabul etmek için bir hizmet sözleşmesinde bir işlemin konusundaki istek belirtir. Özniteliği aşağıdaki özelliğiyle bu denetimi sağlar: hareketleri kullanmak <xref:System.ServiceModel.TransactionFlowOption> gelen bir işlem olup olmadığını belirtmek için numaralandırma <xref:System.ServiceModel.TransactionFlowOption.Mandatory>, <xref:System.ServiceModel.TransactionFlowOption.Allowed>, veya <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>.  
  
 Bu hizmet işlemleri dış etkileşimleri istemcisi ile ilişkili yalnızca bir özniteliğidir. Aşağıdaki bölümlerde açıklanan öznitelikleri hareketleri işlemin yürütülmesini içinde kullanımını ilgilidir.  
  
## <a name="servicebehaviorattribute"></a>ServiceBehaviorAttribute  
 <xref:System.ServiceModel.ServiceBehaviorAttribute> Özniteliği, bir hizmet sözleşmesini uygulama iç yürütme davranışını belirtir. Bu öznitelik işlem özgü özellikleri içerir:  
  
-   <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionAutoCompleteOnSessionClose%2A>oturumu kapattığında tamamlanmamış bir işlemi tamamlamak belirtir. Bu özellik için varsayılan değer `false`. Bu özellik ise `true`ve gelen oturum düzgün biçimde ağ veya istemci nedeniyle hataları kapatma yerine kapatıldı, tamamlanmamış herhangi bir işlem başarıyla tamamlandı. Aksi takdirde, bu özellik ise `false` veya oturum düzgün bir şekilde kapatılmadı, geri oturumu kapattığında herhangi tamamlanmamış işlem alındı. Bu özellik ise `true`, gelen kanal oturum tabanlı olmalıdır.  
  
-   <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A>bir işlem tamamlandığında, temel alınan hizmet örneği yayımlanan olup olmadığını belirtir. Bu özellik için varsayılan değer `true`. Sonraki gelen iletiyi oluşturulması yeni bir temel örnek, önceki örnek tutulan herhangi bir işlem başına durum atıldıktan neden olur. Bir hizmet örneği serbest hizmeti alır ve herhangi bir varolan bağlantılar veya istemcileri grubu oluşturduk oturumlar üzerinde hiçbir etkisi olmaz bir iç eylemdir. Bu işlevsellik sağlayan COM + tam zamanında etkinleştirme özelliği eşdeğerdir. Özellik ise `true`, <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> eşit olmalı <xref:System.ServiceModel.ConcurrencyMode.Single>. Aksi takdirde, hizmet başlatma sırasında geçersiz yapılandırma doğrulama özel durum oluşturur.  
  
-   <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A>Hizmet içinde işlemlerinde kullanılacak yalıtım düzeyini belirtir; Bu özellik birini alır <xref:System.Transactions.IsolationLevel> değerleri. Yerel yalıtım düzeyi özelliği dışındaki herhangi bir şey olması durumunda <xref:System.Transactions.IsolationLevel.Unspecified>, gelen bir işlem yalıtım düzeyi bu yerel özellik ayarı eşleşmesi gerekir. Aksi durumda, gelen işlem reddedilir ve bir arıza istemcisine geri gönderilir. Varsa <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> olan `true`, ve hiçbir işlem akışı yapılan işlem, bu özellik belirler <xref:System.Transactions.IsolationLevel> yerel olarak oluşturulan işlem için kullanılacak bir değer. Varsa <xref:System.Transactions.IsolationLevel> ayarlanır <xref:System.Transactions.IsolationLevel.Unspecified>, <xref:System.Transactions.IsolationLevel> <xref:System.Transactions.IsolationLevel.Serializable> kullanılır.  
  
-   <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A>içinde hizmeti oluşturulmuş yeni bir işlemin tamamlanması gereken süreyi belirtir. Bu kez ulaştı ve işlem tamamlanmadı, iptal edilecek. <xref:System.TimeSpan> Olarak kullanılan <xref:System.Transactions.TransactionScope> sahip herhangi bir işlem için zaman aşımı <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> kümesine `true` ve yeni bir işlem oluşturulduğu için. Zaman aşımı tamamlanması Aşama 1 iki aşamalı yürütme protokolü için işlem oluşturma izin verilen en uzun süreyi ' dir. Kullanılan zaman aşımı değeri her zaman arasında daha düşük değer olan <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> özelliği ve `transactionTimeout` yapılandırma ayarı.  
  
## <a name="operationbehaviorattribute"></a>OperationBehaviorAttribute  
 <xref:System.ServiceModel.OperationBehaviorAttribute> Özniteliği, hizmet uygulamasında yöntemleri davranışlarını belirtir. İşlemin belirli yürütme davranışını belirtmek için kullanabilirsiniz. Bu öznitelik özelliklerini Web hizmeti Açıklama Dili (WSDL) açıklama hizmet sözleşmesinin etkilemez ve tamamen öğeleridir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] geliştiriciler aksi uygulamak zorunda ortak özellikleri etkinleştirmek programlama modeli kendilerini.  
  
 Bu öznitelik aşağıdaki işlem özgü özelliklere sahiptir:  
  
-   <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>bir yöntem bir etkin işlem kapsamı içinde yürütülmeye olup olmadığını belirtir. Varsayılan, `false` değeridir. Varsa <xref:System.ServiceModel.OperationBehaviorAttribute> özniteliği için bir yöntem ayarlı değil, aynı zamanda yöntemi bir işlem içinde yürütmez gelir. Bir işlem kapsamı için bir işlem gerekli değilse, ileti üstbilgisi içinde mevcut herhangi bir işlem değil etkinleştirilir ve bir öğe kalır <xref:System.ServiceModel.OperationContext.IncomingMessageProperties%2A> , <xref:System.ServiceModel.OperationContext>. Bir işlem için bir işlem kapsamı gerekiyorsa, kaynak işlem için aşağıdakilerden birini elde edilir:  
  
    -   Bir işlem istemciden aktarılan, yöntem, dağıtılmış işlem kullanılarak oluşturulan bir işlem kapsamı altında yürütülür.  
  
    -   Sıraya alınan bir aktarım ile ileti dequeue için kullanılan işlem kullanılır. İleti özgün gönderen tarafından sağlanmadı, kullanılan işlem akışlı bir işlem olduğunu unutmayın.  
  
    -   Özel bir taşıma işlemi kullanılarak sağlayabilir `TransportTransactionProperty`.  
  
    -   Yukarıdakilerin hiçbiri bir işlem için bir dış kaynağa sağlarsa, yeni bir <xref:System.Transactions.Transaction> örneği hemen bir yöntemini çağırmadan önce oluşturulur.  
  
-   <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A>hiçbir işlenmeyen özel durumlar varsa, yöntem yürütür işlem otomatik olarak tamamlandı olup olmadığını belirtir. Bu özellik ise `true`, arama altyapısı otomatik olarak "kullanıcı yöntemi bir özel durum oluşturmadan döndürürse tamamlandı"olarak hareket işaretler. Bu özellik ise `false`, işlem örneğine eklenir ve yalnızca "istemci bu özellik ile eşit olarak işaretlenmiş bir sonraki yöntemini çağırırsa tamamlandı"olarak işaretlenmiş `true`, veya bir sonraki yöntem açıkça çağırırsa<xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A>. Bunlardan gerçekleştirmek için hata hiçbir zaman "tamamlandığı" işlemde sonuçları ve içerdiği iş sürece kaydedilmiş, değildir <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionAutoCompleteOnSessionClose%2A> özelliği ayarlanmış `true`. Bu özellik ayarlanmışsa `true`, bir oturum ile bir kanal kullanmanız gerekir ve <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> ayarlanmalıdır <xref:System.ServiceModel.InstanceContextMode.PerSession>.
