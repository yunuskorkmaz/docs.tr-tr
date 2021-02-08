---
description: 'Daha fazla bilgi edinin: ServiceModel Işlem öznitelikleri'
title: ServiceModel İşlem Öznitelikleri
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF], ServiceModel attributes
ms.assetid: 1e0d2436-6ae5-439b-9765-a448d6f60000
ms.openlocfilehash: 0b443fc6b9503007574608afe03c5e0508f666d9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793486"
---
# <a name="servicemodel-transaction-attributes"></a>ServiceModel İşlem Öznitelikleri

Windows Communication Foundation (WCF) <xref:System.ServiceModel> , BIR WCF hizmeti için işlem davranışlarını yapılandırmanıza olanak tanıyan üç standart özniteliğe özellikler sağlar:

- <xref:System.ServiceModel.TransactionFlowAttribute>

- <xref:System.ServiceModel.ServiceBehaviorAttribute>

- <xref:System.ServiceModel.OperationBehaviorAttribute>

## <a name="transactionflowattribute"></a>TransactionFlowAttribute

<xref:System.ServiceModel.TransactionFlowAttribute>Özniteliği bir istemciden gelen işlemleri kabul etmek için bir hizmet sözleşmesindeki bir işlemin kullanımını belirtir. Öznitelik, bu denetimi aşağıdaki özellikle sağlar: Işlemler, <xref:System.ServiceModel.TransactionFlowOption> bir gelen işlemin, veya olduğunu belirtmek için sabit listesini kullanır <xref:System.ServiceModel.TransactionFlowOption.Mandatory> <xref:System.ServiceModel.TransactionFlowOption.Allowed> <xref:System.ServiceModel.TransactionFlowOption.NotAllowed> .

Bu, hizmet işlemlerini bir istemciyle dış etkileşimlerle ilişkilendiren tek özniteliktir. Aşağıdaki bölümlerde açıklanan öznitelikler işlemin yürütülmesi içinde işlemlerin kullanımıyla ilgilidir.

## <a name="servicebehaviorattribute"></a>ServiceBehaviorAttribute

<xref:System.ServiceModel.ServiceBehaviorAttribute>Öznitelik, bir hizmet sözleşmesi uygulamasının iç yürütme davranışını belirtir. Bu özniteliğin işleme özgü özellikleri şunlardır:

- <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionAutoCompleteOnSessionClose%2A> oturum kapandığında tamamlanmamış bir işlemin tamamlanıp tamamlanmayacağını belirtir. Bu özellik için varsayılan değer `false` . Bu özellik ise `true` ve ağ veya istemci arızalarının kapanması yerine gelen oturum düzgün şekilde kapatılırsa, tamamlanmamış işlemler başarıyla tamamlanır. Aksi takdirde, bu özellik ise `false` veya oturum düzgün şekilde kapatılmazsa, oturum kapandığında tamamlanmamış işlem geri alınır. Bu özellik ise `true` , gelen kanalın oturum tabanlı olması gerekir.

- <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> işlem tamamlandığında temeldeki hizmet örneğinin serbest bırakılıp başlatılmayacağını belirtir. Bu özellik için varsayılan değer `true` . Sonraki gelen ileti, yeni bir temel örneğin oluşturulmasına neden olur ve önceki örneğin işlem başına durumu atılıyor. Hizmet örneğini serbest bırakmak, hizmetin aldığı ve istemcilerin oluşturmuş olabileceği herhangi bir bağlantıyı veya oturumu üzerinde hiçbir etkisi olmayan bir iç işlemdir. Bu işlevsellik, tek seferlik etkinleştirme özelliği COM+ tarafından sağlanır. Özelliği ise `true` , <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> değerine eşit olmalıdır <xref:System.ServiceModel.ConcurrencyMode.Single> . Aksi takdirde, hizmet başlatma sırasında geçersiz bir yapılandırma doğrulama özel durumu oluşturur.

- <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> hizmet içindeki işlemler için kullanılacak yalıtım düzeyini belirtir; Bu özellik değerlerden birini alır <xref:System.Transactions.IsolationLevel> . Yerel yalıtım düzeyi özelliği dışında herhangi <xref:System.Transactions.IsolationLevel.Unspecified> bir şeydir, bir gelen işlemin yalıtım düzeyi bu yerel özelliğin ayarıyla eşleşmelidir. Aksi takdirde, gelen işlem reddedilir ve istemciye bir hata gönderilir. <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>İse `true` ve hiçbir işlem akıtılıp, bu özellik <xref:System.Transactions.IsolationLevel> yerel olarak oluşturulan işlem için kullanılacak değeri belirler. Olarak <xref:System.Transactions.IsolationLevel> ayarlanırsa <xref:System.Transactions.IsolationLevel.Unspecified> , <xref:System.Transactions.IsolationLevel> <xref:System.Transactions.IsolationLevel.Serializable> kullanılır.

- <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> hizmette oluşturulan yeni bir işlemin tamamlanma süresini belirtir. Bu saate ulaşılırsa ve işlem tamamlandıysa, iptal edilir. , <xref:System.TimeSpan> <xref:System.Transactions.TransactionScope> <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> Olarak ayarlanmış `true` ve yeni bir işlem oluşturulduğu işlemler için zaman aşımı olarak kullanılır. Zaman aşımı, iki aşamalı işleme protokolünde işlem 1 ' in tamamlanmasına kadar işlemin oluşturulmasının izin verilen en uzun süredir. Kullanılan zaman aşımı değeri her zaman <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> özellik ve yapılandırma ayarı arasındaki alt değerdir `transactionTimeout` .

## <a name="operationbehaviorattribute"></a>OperationBehaviorAttribute

<xref:System.ServiceModel.OperationBehaviorAttribute>Öznitelik, hizmet uygulamasındaki yöntemlerin davranışlarını belirtir. İşlemin belirli yürütme davranışını göstermek için kullanabilirsiniz. Bu özniteliğin özellikleri, hizmet sözleşmesinin Web hizmeti Açıklama Dili (WSDL) açıklamasını etkilemez ve yalnızca WCF programlama modelinin, geliştiricilerin diğer koşullarda kendilerini uygulamak zorunda olduğu ortak özellikleri etkinleştiren öğelerdir.

Bu öznitelik, işleme özgü aşağıdaki özelliklere sahiptir:

- <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> bir yöntemin etkin bir işlem kapsamı içinde yürütülüp yürütülmeyeceğini belirtir. Varsayılan değer: `false`. <xref:System.ServiceModel.OperationBehaviorAttribute>Özniteliği bir yöntem için ayarlanmamışsa, yöntemin bir işlemde yürütülmeyeceğini de belirtir. İşlem kapsamı bir işlem için gerekli değilse, ileti üstbilgisinde bulunan herhangi bir işlem etkinleştirilmemiştir ve öğesinin öğesi olarak kalır <xref:System.ServiceModel.OperationContext.IncomingMessageProperties%2A> <xref:System.ServiceModel.OperationContext> . Bir işlem için işlem kapsamı gerekliyse, işlemin kaynağı aşağıdakilerden birinden türetilir:

  - Bir işlem istemciden akıtılırsa, yöntemi bu dağıtılmış işlem kullanılarak oluşturulan bir işlem kapsamında yürütülür.

  - Sıraya alınmış bir aktarımla, iletiyi sıradan çıkarma işleminde kullanılan işlem kullanılır. Kullanılan işlemin bir akışlı işlem değil, iletinin özgün gönderici tarafından sağlanmadığını unutmayın.

  - Özel bir aktarım, kullanarak bir işlem sağlayabilir `TransportTransactionProperty` .

  - Yukarıdakilerin hiçbiri bir işlem için dış kaynak sunmadıysa, <xref:System.Transactions.Transaction> yöntemi çağrılmadan hemen önce yeni bir örnek oluşturulur.

- <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> İşlenmeyen özel durumlar oluşursa, yöntemin yürütüldüğü işlemin otomatik olarak tamamlanıp tamamlanmadığını belirtir. Bu özellik ise, `true` Kullanıcı yöntemi özel durum oluşturmadan döndürürse, çağıran altyapı otomatik olarak işlemi "tamamlandı" olarak işaretler. Bu özellik ise, `false` işlem örneğe iliştirilir ve yalnızca istemci bu özellikle eşit olarak işaretlenen bir sonraki yöntemi çağırırsa `true` veya sonraki bir yöntem açıkça çağırırsa "tamamlandı" olarak işaretlenir <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> . İşlem içinde bu sonuçlardan herhangi birini gerçekleştirmeme, hiçbir durumda "tamamlanmadı" ve bu özellik olarak ayarlanmadığı takdirde içerilen iş yürütülmedi <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionAutoCompleteOnSessionClose%2A> `true` . Bu özellik olarak ayarlandıysa `true` , oturum içeren bir kanal kullanmanız gerekir ve <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> olarak ayarlanmalıdır <xref:System.ServiceModel.InstanceContextMode.PerSession> .
