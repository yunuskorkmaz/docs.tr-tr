---
title: ServiceModel İşlem Öznitelikleri
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF], ServiceModel attributes
ms.assetid: 1e0d2436-6ae5-439b-9765-a448d6f60000
ms.openlocfilehash: d4b7482431404241577111d8dd3841319b65696e
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663689"
---
# <a name="servicemodel-transaction-attributes"></a>ServiceModel İşlem Öznitelikleri

Windows Communication Foundation (WCF) üç standardını temel özellikleri sağlar <xref:System.ServiceModel> , bir WCF hizmeti için işlem davranışını yapılandırmanızı sağlayan öznitelikler:

- <xref:System.ServiceModel.TransactionFlowAttribute>

- <xref:System.ServiceModel.ServiceBehaviorAttribute>

- <xref:System.ServiceModel.OperationBehaviorAttribute>

## <a name="transactionflowattribute"></a>TransactionFlowAttribute

<xref:System.ServiceModel.TransactionFlowAttribute> Öznitelik, bir istemciden gelen işlem kabul etmek için bir hizmet sözleşmesinde bir işlemin tartışabilir belirtir. Öznitelik, aşağıdaki özelliklerle bu denetimi sağlar: İşlemleri kullanma <xref:System.ServiceModel.TransactionFlowOption> gelen bir işlem olup olmadığını belirlemek için numaralandırma <xref:System.ServiceModel.TransactionFlowOption.Mandatory>, <xref:System.ServiceModel.TransactionFlowOption.Allowed>, veya <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>.

Hizmet istemcisi ile dış etkileşimleri işlemleriyle yalnızca özniteliğidir. Aşağıdaki bölümlerde açıklanan öznitelikleri işlem yürütme işlemi içinde kullanımı ile ilgilidir.

## <a name="servicebehaviorattribute"></a>ServiceBehaviorAttribute

<xref:System.ServiceModel.ServiceBehaviorAttribute> Özniteliği, bir hizmet sözleşmesini uygulama iç yürütme davranışını belirtir. Bu özniteliğin işlem özgü özellikler şunlardır:

- <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionAutoCompleteOnSessionClose%2A> oturumu kapattığında tamamlanmamış bir hareketi tamamlamak belirtir. Bu özellik için varsayılan değer `false`. Bu özellik ise `true`ve gelen oturum düzgün bir şekilde ağ veya istemci nedeniyle, hataları kapatma yerine kapatıldı, tamamlanmamış herhangi bir işlemi başarıyla tamamlandı. Aksi takdirde bu özelliği ise `false` veya oturumu düzgün bir şekilde kapatılmamış, geri oturumu kapattığında tamamlanmamış her türlü işleme alınır. Bu özellik ise `true`, gelen kanal oturum tabanlı olmalıdır.

- <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> İşlem tamamlandığında, temel alınan hizmet örneği serbest olup olmadığını belirtir. Bu özellik için varsayılan değer `true`. Sonraki gelen iletiyi oluşturulacak yeni bir temel örnek, önceki örneği tutulan herhangi bir işlem başına durumu atılıyor neden olur. Bir hizmet örneği serbest hizmeti alır ve herhangi bir mevcut bağlantıları veya istemciler yerleşik olduğu oturumları etkilemez bir iç işlemdir. Bu işlevsellik sağlayan COM + just-ın-time etkinleştirme özelliği eşdeğerdir. Özellik ise `true`, <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> eşit olmalı <xref:System.ServiceModel.ConcurrencyMode.Single>. Aksi takdirde, hizmet başlatma sırasında bir geçersiz yapılandırma doğrulama özel durum oluşturur.

- <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> Hizmet işlemleri için kullanılacak yalıtım düzeyini belirtir. Bu özellik birini alır <xref:System.Transactions.IsolationLevel> değerleri. Yerel yalıtım düzeyi özelliği dışında herhangi bir şey olması durumunda <xref:System.Transactions.IsolationLevel.Unspecified>, gelen bir işlem yalıtım düzeyi bu yerel özellik ayarı eşleşmelidir. Aksi takdirde, gelen işlem reddedilir ve bir arıza istemciye geri gönderilir. Varsa <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> olduğu `true`, ve bu özellik hiçbir işlem kimliğini, belirler <xref:System.Transactions.IsolationLevel> yerel olarak oluşturulan işlem için kullanılacak değer. Varsa <xref:System.Transactions.IsolationLevel> ayarlanır <xref:System.Transactions.IsolationLevel.Unspecified>, <xref:System.Transactions.IsolationLevel> <xref:System.Transactions.IsolationLevel.Serializable> kullanılır.

- <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> içinde hizmeti oluşturulan yeni bir işlemin tamamlanması gereken süreyi belirtir. Bu kez ulaştı ve işlem tamamlandı, iptal edilecek. <xref:System.TimeSpan> Olarak kullanılan <xref:System.Transactions.TransactionScope> sahip herhangi bir işlem için zaman aşımını <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> kümesine `true` ve yeni bir işlem oluşturulduğu için. Zaman aşımı oluşturma işlem izin verilen en uzun süresi iki aşamalı tamamlama protokolü 1 aşamasında tamamlanması için ' dir. Kullanılan zaman aşımı değeri her zaman daha düşük bir değer arasında olduğu <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> özelliği ve `transactionTimeout` yapılandırma ayarı.

## <a name="operationbehaviorattribute"></a>OperationBehaviorAttribute

<xref:System.ServiceModel.OperationBehaviorAttribute> Özniteliği hizmet uygulamasında yöntemleri davranışlarını belirtir. İşlem yürütme davranışını belirtmek için kullanabilirsiniz. Bu öznitelik özelliklerini Web hizmeti Açıklama Dili (WSDL) açıklama hizmet sözleşmesinin etkilemez ve aksi geliştiricileri kendilerini uygulamak sahip ortak özellikler sağlayan tamamen WCF programlama modeli öğeleridir.

Bu öznitelik, aşağıdaki işlem özgü özelliklere sahiptir:

- <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> bir yöntem bir etkin işlem kapsamı içinde yürütülmeye olup olmadığını belirtir. Varsayılan, `false` değeridir. Varsa <xref:System.ServiceModel.OperationBehaviorAttribute> özniteliği için bir yöntem ayarlı değil, ayrıca yöntemi bir işlem yürütmez gösterir. İşlem kapsamı için bir işlem gerekli değilse, ileti üst bilgisi içinde mevcut olan herhangi bir işlem etkin ve bir öğesi olarak kalır <xref:System.ServiceModel.OperationContext.IncomingMessageProperties%2A> , <xref:System.ServiceModel.OperationContext>. İşlem kapsamı için bir işlem gerekliyse, kaynak işlem için aşağıdakilerden birini elde edilir:

  - Bir işlem, istemciden aktarılan, yöntem, dağıtılmış bir işlem kullanılarak oluşturulan bir işlem kapsamı altında yürütülür.

  - İletiyi sıradan çıkar için kullanılan işlem bir kuyruğa alınmış taşıma ile kullanılır. Özgün iletinin gönderen tarafından sağlanmadı, kullanılan işlem akışlı bir işlem olmadığını unutmayın.

  - Bir işlem kullanılarak özel bir taşıma sağlayabilir `TransportTransactionProperty`.

  - Yukarıdakilerin hiçbiri bir işlem için bir dış kaynaktan sağlıyorsa, yeni bir <xref:System.Transactions.Transaction> örneği, hemen bir yöntemini çağırmadan önce oluşturulur.

- <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> Eğer işlenmeyen özel durumlar harekete yöntemi yürütür işlem otomatik olarak tamamlanıp tamamlanmadığını belirtir. Bu özellik ise `true`, çağıran altyapı otomatik olarak "kullanıcı yöntemi bir özel durum oluşturmadan döndürürse tamamlandı olarak" işlem işaretler. Bu özellik ise `false`, işlem örneğine eklenir ve yalnızca "istemci bu özellik ile eşit olarak işaretlenmiş bir sonraki yöntemi çağırması durumunda tamamlandı olarak" işaretlenir `true`, veya bir sonraki yöntemi açıkça çağırırsa<xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A>. Bunlardan birini gerçekleştirmek için hata hiçbir zaman "" işlem tamamlandı sonuçları gruplayan ve içerdiği iş sürece, kaydedilmedi <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionAutoCompleteOnSessionClose%2A> özelliği `true`. Bu özellik ayarlanırsa `true`, oturum, bir kanal kullanmanız gerekir ve <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> ayarlanmalıdır <xref:System.ServiceModel.InstanceContextMode.PerSession>.
