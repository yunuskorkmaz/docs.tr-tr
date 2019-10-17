---
title: Koruma Düzeylerini Anlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
- ProtectionLevel property
ms.assetid: 0c034608-a1ac-4007-8287-b1382eaa8bf2
ms.openlocfilehash: 896b75d3dfb5ebace9bef0c410e4a86dfb765bd8
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321523"
---
# <a name="understanding-protection-level"></a>Koruma Düzeylerini Anlama

@No__t-0 özelliği, <xref:System.ServiceModel.ServiceContractAttribute> ve <xref:System.ServiceModel.OperationContractAttribute> sınıfları gibi birçok farklı sınıfta bulunur. Özelliği, bir iletinin bölümünün (veya tamamının) nasıl korunduğunu denetler. Bu konu, Windows Communication Foundation (WCF) özelliğini ve nasıl çalıştığını açıklamaktadır.

Koruma düzeyini ayarlamayla ilgili yönergeler için bkz. [nasıl yapılır: ProtectionLevel özelliğini ayarlama](how-to-set-the-protectionlevel-property.md).

> [!NOTE]
> Koruma düzeyleri, yapılandırmada değil yalnızca kodda ayarlanabilir.

## <a name="basics"></a>Temel bilgileri

Koruma düzeyi özelliğini anlamak için aşağıdaki temel deyimler geçerlidir:

- Bir iletinin herhangi bir bölümünde üç temel koruma düzeyi vardır. Özelliği (nerede olursa olsun) <xref:System.Net.Security.ProtectionLevel> sabit listesi değerlerinden birine ayarlanır. Artan koruma sırasıyla şunları içerir:

  - `None`.

  - `Sign`. Korunan bölüm dijital olarak imzalanır. Bu, korumalı ileti bölümü ile yapılan tüm değişiklikleri algılamayı sağlar.

  - `EncryptAndSign`. İleti bölümü, imzalanmadan önce gizliliği sağlamak için şifrelenir.

- Koruma gereksinimlerini yalnızca bu özelliğe sahip *uygulama verileri* için ayarlayabilirsiniz. Örneğin, WS-Addressing üst bilgileri altyapı verileri olduğundan, bu nedenle `ProtectionLevel` ' ı etkilemez.

- Güvenlik modu `Transport` olarak ayarlandığında, tüm ileti taşıma mekanizması tarafından korunur. Bu nedenle, bir iletinin farklı bölümlerinin ayrı bir koruma düzeyini ayarlamanın hiçbir etkisi olmaz.

- @No__t-0, geliştiricinin bir bağlamanın uyması gereken *En düşük düzeyi* ayarlaması için bir yoldur. Bir hizmet dağıtıldığında, yapılandırmada belirtilen gerçek bağlama en düşük düzeyi destekleyebilir veya desteklemiyor olabilir. Örneğin, varsayılan olarak <xref:System.ServiceModel.BasicHttpBinding> sınıfı güvenlik sağlamaz (etkinleştirilebilir, ancak). Bu nedenle, bunu `None` dışında bir ayar içeren bir sözleşmeyle kullanmak özel durumun oluşturulmasına neden olur.

- Hizmet, tüm iletiler için en düşük `ProtectionLevel` ' ı `Sign` ' i gerektiriyorsa, bir istemci (Belki de WCF olmayan bir teknoloji tarafından oluşturulan) tüm iletileri şifreleyebilir ve imzalayabilirler (en düşük gerekenden daha fazla). Bu durumda, istemci en düşük boyuttan daha fazla işlem yaptığından WCF bir özel durum oluşturmaz. Ancak, WCF uygulamalarının (hizmetler veya istemciler) mümkünse bir ileti bölümünün güvenli olmadığını, ancak en düşük düzeye uyum olacağını unutmayın. Ayrıca, güvenlik modu olarak `Transport` kullanırken, aktarım, daha ayrıntılı bir düzeyde güvenli bir şekilde güvenli hale uğradığından ileti akışının aşırı güvenli olabileceğini unutmayın.

- @No__t-0 ' ı açıkça `Sign` veya `EncryptAndSign` olarak ayarlarsanız, güvenliği etkinleştirilmiş bir bağlama kullanmanız gerekir veya bir özel durum oluşturulur.

- Güvenlik sağlayan bir bağlama seçerseniz ve `ProtectionLevel` özelliğini sözleşmede herhangi bir yere ayarlamayın, tüm uygulama verileri şifrelenir ve imzalanır.

- Güvenlik etkin olmayan bir bağlama seçerseniz (örneğin, `BasicHttpBinding` sınıfı varsayılan olarak güvenlik devre dışı bırakılır) ve `ProtectionLevel` açıkça ayarlanmamışsa, uygulama verilerinden hiçbiri korunmaz.

- Aktarım düzeyinde güvenlik uygulayan bir bağlama kullanıyorsanız, tüm uygulama verileri taşımanın özelliklerine göre güvence altına alınır.

- İleti düzeyinde güvenlik uygulayan bir bağlama kullanırsanız, uygulama verileri sözleşmede ayarlanan koruma düzeylerine göre güvenlik altına alınır. Koruma düzeyi belirtmezseniz, iletilerdeki tüm uygulama verileri şifrelenir ve imzalanacaktır.

- @No__t-0 farklı kapsam düzeylerinde ayarlanabilir. Bir sonraki bölümde açıklanan, kapsam ile ilişkili bir hiyerarşi vardır.

## <a name="scoping"></a>Kapsamlar

En üstteki API üzerinde `ProtectionLevel` ayarlandığında, altındaki tüm düzeylerin düzeyi ayarlanır. @No__t-0 ' ı daha düşük bir düzeyde farklı bir değere ayarlandıysa, hiyerarşide o düzeyin altındaki tüm API 'Ler artık yeni düzeye sıfırlanacak (ancak yukarıdaki API 'Ler, en üst düzeyden etkilenmeye devam edecektir). Hiyerarşi aşağıdaki gibidir. Aynı düzeydeki öznitelikler eşler.

- <xref:System.ServiceModel.ServiceContractAttribute>

- <xref:System.ServiceModel.OperationContractAttribute>

- <xref:System.ServiceModel.FaultContractAttribute>

- <xref:System.ServiceModel.MessageContractAttribute>

- <xref:System.ServiceModel.MessageHeaderAttribute>

- <xref:System.ServiceModel.MessageBodyMemberAttribute>

## <a name="programming-protectionlevel"></a>ProtectionLevel programlama

Hiyerarşinin herhangi bir noktasında `ProtectionLevel` ' ı programlamak için, özniteliği uygularken özelliği uygun bir değere ayarlamanız yeterlidir. Örnekler için bkz. [nasıl yapılır: ProtectionLevel özelliğini ayarlama](how-to-set-the-protectionlevel-property.md).

> [!NOTE]
> Hatalar ve ileti sözleşmeleri üzerinde özelliğin ayarlanması, bu özelliklerin nasıl çalıştığını anlamayı gerektirir. Daha fazla bilgi için bkz. [nasıl yapılır: ProtectionLevel özelliğini ayarlama](how-to-set-the-protectionlevel-property.md) ve [ileti sözleşmelerini kullanma](./feature-details/using-message-contracts.md).

## <a name="ws-addressing-dependency"></a>WS-Addressing bağımlılığı

Çoğu durumda, istemci oluşturmak için [ServiceModel meta veri yardımcı programı aracını (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) kullanmak, istemci ve hizmet sözleşmelerinin aynı olmasını sağlar. Ancak, benzer sözleşmeler istemcinin özel durum oluşturmasına neden olabilir. Bu, bir bağlama WS-Addressing belirtimini desteklemediğinde ve sözleşmede birden çok koruma düzeyi belirtildiğinde oluşur. Örneğin, <xref:System.ServiceModel.BasicHttpBinding> sınıfı belirtimi desteklemez ya da WS-Addressing desteklemeyen özel bir bağlama oluşturursanız. @No__t-0 özelliği, tek bir sözleşmede farklı koruma düzeylerini etkinleştirmek için WS-Addressing belirtimine dayanır. Bağlama WS-Addressing belirtimini desteklemiyorsa, tüm düzeyler aynı koruma düzeyi olarak ayarlanır. Sözleşmede tüm kapsamlar için etkili koruma düzeyi, sözleşmede kullanılan en güçlü koruma düzeyine ayarlanır.

Bu, ilk bakışta hata ayıklamanın zor olduğu bir soruna neden olabilir. Birden fazla hizmet için yöntemler içeren bir istemci Sözleşmesi (arabirim) oluşturmak mümkündür. Diğer bir deyişle, aynı arabirim birçok hizmetle iletişim kuran bir istemci oluşturmak için kullanılır ve tek arabirim tüm hizmetler için yöntemler içerir. Geliştirici, yalnızca belirli bir hizmet için geçerli olan yöntemleri çağırmak üzere bu nadir senaryoda dikkatli olmalıdır. Bağlama <xref:System.ServiceModel.BasicHttpBinding> sınıfı ise, birden çok koruma düzeyi desteklenemez. Ancak, istemciye yanıt veren bir hizmet, gerekli olandan daha düşük bir koruma düzeyiyle istemciye yanıt verebilir. Bu durumda, istemci daha yüksek bir koruma düzeyi beklediği için bir özel durum oluşturur.

Bu sorunu gösteren bir kod örneği. Aşağıdaki örnek bir hizmeti ve bir istemci sözleşmesini gösterir. Bağlamanın [\<basicHttpBinding >](../configure-apps/file-schema/wcf/basichttpbinding.md) öğesi olduğunu varsayalım. Bu nedenle, bir sözleşmede tüm işlemlerin aynı koruma düzeyi vardır. Bu tek düzen koruma düzeyi, tüm işlemlerde en yüksek koruma düzeyi olarak belirlenir.

Hizmet Sözleşmesi:

[!code-csharp[c_ProtectionLevel#7](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#7)]
[!code-vb[c_ProtectionLevel#7](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#7)]

Aşağıdaki kod, istemci sözleşmesi arabirimini gösterir. Bunun farklı bir hizmetle kullanılması amaçlanan bir `Tax` yöntemi içerdiğini unutmayın:

[!code-csharp[c_ProtectionLevel#8](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#8)]
[!code-vb[c_ProtectionLevel#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#8)]

İstemci `Price` yöntemini çağırdığında hizmetten bir yanıt aldığında bir özel durum oluşturur. Bu durum, istemcinin `ServiceContractAttribute` üzerinde bir `ProtectionLevel` belirtmediği ve bu nedenle istemci, `Price` yöntemi de dahil tüm yöntemler için varsayılan (<xref:System.Net.Security.ProtectionLevel.EncryptAndSign>) kullanır. Ancak hizmet sözleşmesi, koruma düzeyi <xref:System.Net.Security.ProtectionLevel.Sign> olarak ayarlanmış tek bir yöntem tanımladığından, hizmet <xref:System.Net.Security.ProtectionLevel.Sign> düzeyi kullanılarak değeri döndürür. Bu durumda, istemci hizmetten gelen yanıtı doğrularken bir hata oluşturur.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- <xref:System.ServiceModel.FaultContractAttribute>
- <xref:System.ServiceModel.MessageContractAttribute>
- <xref:System.ServiceModel.MessageHeaderAttribute>
- <xref:System.ServiceModel.MessageBodyMemberAttribute>
- <xref:System.Net.Security.ProtectionLevel>
- [Hizmetleri Güvenli Hale Getirme](securing-services.md)
- [Nasıl yapılır: ProtectionLevel Özelliğini Ayarlama](how-to-set-the-protectionlevel-property.md)
- [Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme](specifying-and-handling-faults-in-contracts-and-services.md)
- [İleti Anlaşmaları Kullanma](./feature-details/using-message-contracts.md)
