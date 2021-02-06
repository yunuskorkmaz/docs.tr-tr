---
description: 'Daha fazla bilgi edinin: koruma düzeyini anlama'
title: Koruma Düzeylerini Anlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
- ProtectionLevel property
ms.assetid: 0c034608-a1ac-4007-8287-b1382eaa8bf2
ms.openlocfilehash: 8c6e5bc97c02e9cec4841dac0d7cf8c8b59931e1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631716"
---
# <a name="understanding-protection-level"></a>Koruma Düzeylerini Anlama

`ProtectionLevel`Özelliği, ve sınıfları gibi birçok farklı sınıfta bulunur <xref:System.ServiceModel.ServiceContractAttribute> <xref:System.ServiceModel.OperationContractAttribute> . Özelliği, bir iletinin bölümünün (veya tamamının) nasıl korunduğunu denetler. Bu konu, Windows Communication Foundation (WCF) özelliğini ve nasıl çalıştığını açıklamaktadır.

Koruma düzeyini ayarlamayla ilgili yönergeler için bkz. [nasıl yapılır: ProtectionLevel özelliğini ayarlama](how-to-set-the-protectionlevel-property.md).

> [!NOTE]
> Koruma düzeyleri, yapılandırmada değil yalnızca kodda ayarlanabilir.

## <a name="basics"></a>Temel bilgiler

Koruma düzeyi özelliğini anlamak için aşağıdaki temel deyimler geçerlidir:

- Bir iletinin herhangi bir bölümünde üç temel koruma düzeyi vardır. Özelliği (nerede olursa olsun) <xref:System.Net.Security.ProtectionLevel> sabit listesi değerlerinden birine ayarlanır. Artan koruma sırasıyla şunları içerir:

  - `None`.

  - `Sign`. Korunan bölüm dijital olarak imzalanır. Bu, korumalı ileti bölümü ile yapılan tüm değişiklikleri algılamayı sağlar.

  - `EncryptAndSign`. İleti bölümü, imzalanmadan önce gizliliği sağlamak için şifrelenir.

- Koruma gereksinimlerini yalnızca bu özelliğe sahip *uygulama verileri* için ayarlayabilirsiniz. Örneğin, WS-Addressing üst bilgileri altyapı verileri olduğundan, bundan etkilenmez `ProtectionLevel` .

- Güvenlik modu olarak ayarlandığında `Transport` , tüm ileti taşıma mekanizması tarafından korunur. Bu nedenle, bir iletinin farklı bölümlerinin ayrı bir koruma düzeyini ayarlamanın hiçbir etkisi olmaz.

- , `ProtectionLevel` Geliştiricinin bir bağlamanın uyması gereken *En düşük düzeyi* ayarlaması için bir yoldur. Bir hizmet dağıtıldığında, yapılandırmada belirtilen gerçek bağlama en düşük düzeyi destekleyebilir veya desteklemiyor olabilir. Örneğin, varsayılan olarak, <xref:System.ServiceModel.BasicHttpBinding> sınıfı güvenlik sağlamaz (etkinleştirilebilir, ancak). Bu nedenle, bunu dışında bir ayarı olan bir sözleşmeyle kullanmak `None` özel durumun oluşturulmasına neden olur.

- Hizmet `ProtectionLevel` tüm iletiler için en düşük değer gerektiriyorsa `Sign` , bir istemci (belkı de WCF olmayan bir teknoloji tarafından oluşturulan) tüm iletileri şifreleyebilir ve imzalayabilir (en düşük gerekenden daha fazla). Bu durumda, istemci en düşük boyuttan daha fazla işlem yaptığından WCF bir özel durum oluşturmaz. Ancak, WCF uygulamalarının (hizmetler veya istemciler) mümkünse bir ileti bölümünün güvenli olmadığını, ancak en düşük düzeye uyum olacağını unutmayın. Ayrıca `Transport` , güvenlik modu olarak kullanıldığında, aktarım, daha ayrıntılı bir düzeyde güvenli bir şekilde güvenli hale uğradığından, ileti akışının aşırı güvenli olabileceğini unutmayın.

- `ProtectionLevel`Açıkça veya ya da olarak ayarlarsanız `Sign` `EncryptAndSign` , güvenliği etkinleştirilmiş bir bağlama kullanmanız gerekir veya bir özel durum oluşturulur.

- Güvenliği sağlayan bir bağlama seçerseniz ve `ProtectionLevel` özelliği sözleşmede herhangi bir yere ayarlamayın, tüm uygulama verileri şifrelenir ve imzalanır.

- Güvenlik etkin olmayan bir bağlama seçerseniz (örneğin, `BasicHttpBinding` sınıf varsayılan olarak güvenlik devre dışı bırakılmışsa) ve `ProtectionLevel` açıkça ayarlanmamışsa, uygulama verilerinden hiçbiri korunmaz.

- Aktarım düzeyinde güvenlik uygulayan bir bağlama kullanıyorsanız, tüm uygulama verileri taşımanın özelliklerine göre güvence altına alınır.

- İleti düzeyinde güvenlik uygulayan bir bağlama kullanırsanız, uygulama verileri sözleşmede ayarlanan koruma düzeylerine göre güvenlik altına alınır. Koruma düzeyi belirtmezseniz, iletilerdeki tüm uygulama verileri şifrelenir ve imzalanacaktır.

- `ProtectionLevel`Farklı kapsam düzeylerinde ayarlanabilir. Bir sonraki bölümde açıklanan, kapsam ile ilişkili bir hiyerarşi vardır.

## <a name="scoping"></a>Kapsamlar

`ProtectionLevel`En ÜSTTEKI API üzerinde ayarlandığında, altındaki tüm düzeylerin düzeyi ayarlanır. `ProtectionLevel`Daha düşük bir düzeyde farklı bir değere ayarlandıysa, hiyerarşide bu düzeyin altındaki tüm API 'ler artık yeni düzeye sıfırlanacak (ancak yukarıdaki API 'ler, en üst düzeyden etkilenmeye devam eder). Hiyerarşi aşağıdaki gibidir. Aynı düzeydeki öznitelikler eşler.

- <xref:System.ServiceModel.ServiceContractAttribute>

- <xref:System.ServiceModel.OperationContractAttribute>

- <xref:System.ServiceModel.FaultContractAttribute>

- <xref:System.ServiceModel.MessageContractAttribute>

- <xref:System.ServiceModel.MessageHeaderAttribute>

- <xref:System.ServiceModel.MessageBodyMemberAttribute>

## <a name="programming-protectionlevel"></a>ProtectionLevel programlama

`ProtectionLevel`Hiyerarşinin herhangi bir noktasında programını programlamak için özniteliği uygularken özelliği uygun bir değere ayarlamanız yeterlidir. Örnekler için bkz. [nasıl yapılır: ProtectionLevel özelliğini ayarlama](how-to-set-the-protectionlevel-property.md).

> [!NOTE]
> Hatalar ve ileti sözleşmeleri üzerinde özelliğin ayarlanması, bu özelliklerin nasıl çalıştığını anlamayı gerektirir. Daha fazla bilgi için bkz. [nasıl yapılır: ProtectionLevel özelliğini ayarlama](how-to-set-the-protectionlevel-property.md) ve [ileti sözleşmelerini kullanma](./feature-details/using-message-contracts.md).

## <a name="ws-addressing-dependency"></a>WS-Addressing bağımlılığı

Çoğu durumda, istemci oluşturmak için [ServiceModel meta veri yardımcı programı aracını (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) kullanmak, istemci ve hizmet sözleşmelerinin aynı olmasını sağlar. Ancak, benzer sözleşmeler istemcinin özel durum oluşturmasına neden olabilir. Bu, bir bağlama WS-Addressing belirtimini desteklemediğinde ve sözleşmede birden çok koruma düzeyi belirtildiğinde oluşur. Örneğin, <xref:System.ServiceModel.BasicHttpBinding> sınıfı belirtimi desteklemez veya ws-Addressing desteklemeyen özel bir bağlama oluşturursanız. `ProtectionLevel`Özelliği, tek bir sözleşmede farklı koruma düzeylerini etkinleştirmek için WS-Addressing belirtimine dayanır. Bağlama WS-Addressing belirtimini desteklemiyorsa, tüm düzeyler aynı koruma düzeyi olarak ayarlanır. Sözleşmede tüm kapsamlar için etkili koruma düzeyi, sözleşmede kullanılan en güçlü koruma düzeyine ayarlanır.

Bu, ilk bakışta hata ayıklamanın zor olduğu bir soruna neden olabilir. Birden fazla hizmet için yöntemler içeren bir istemci Sözleşmesi (arabirim) oluşturmak mümkündür. Diğer bir deyişle, aynı arabirim birçok hizmetle iletişim kuran bir istemci oluşturmak için kullanılır ve tek arabirim tüm hizmetler için yöntemler içerir. Geliştirici, yalnızca belirli bir hizmet için geçerli olan yöntemleri çağırmak üzere bu nadir senaryoda dikkatli olmalıdır. Bağlama <xref:System.ServiceModel.BasicHttpBinding> sınıfınise, birden çok koruma düzeyi desteklenemez. Ancak, istemciye yanıt veren bir hizmet, gerekli olandan daha düşük bir koruma düzeyiyle istemciye yanıt verebilir. Bu durumda, istemci daha yüksek bir koruma düzeyi beklediği için bir özel durum oluşturur.

Bu sorunu gösteren bir kod örneği. Aşağıdaki örnek bir hizmeti ve bir istemci sözleşmesini gösterir. Bağlamanın öğe olduğunu varsayın [\<basicHttpBinding>](../configure-apps/file-schema/wcf/basichttpbinding.md) . Bu nedenle, bir sözleşmede tüm işlemlerin aynı koruma düzeyi vardır. Bu tek düzen koruma düzeyi, tüm işlemlerde en yüksek koruma düzeyi olarak belirlenir.

Hizmet Sözleşmesi:

[!code-csharp[c_ProtectionLevel#7](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#7)]
[!code-vb[c_ProtectionLevel#7](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#7)]

Aşağıdaki kod, istemci sözleşmesi arabirimini gösterir. Bunun `Tax` farklı bir hizmetle kullanılması amaçlanan bir yöntemi içerdiğini unutmayın:

[!code-csharp[c_ProtectionLevel#8](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#8)]
[!code-vb[c_ProtectionLevel#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#8)]

İstemci `Price` yöntemi çağırdığında, hizmetten bir yanıt aldığında bir özel durum oluşturur. Bunun nedeni, istemcisinin ' de bir `ProtectionLevel` ' i belirtmediği `ServiceContractAttribute` ve bu nedenle istemci, <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> yöntemi dahil tüm yöntemler için varsayılan () kullanır `Price` . Ancak, hizmet <xref:System.Net.Security.ProtectionLevel.Sign> sözleşmesi koruma düzeyi olarak ayarlanmış tek bir yöntem tanımladığından, hizmet bu düzeyi kullanarak değeri döndürür <xref:System.Net.Security.ProtectionLevel.Sign> . Bu durumda, istemci hizmetten gelen yanıtı doğrularken bir hata oluşturur.

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
- [İleti Sözleşmeleri Kullanılıyor](./feature-details/using-message-contracts.md)
