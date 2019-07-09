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
ms.openlocfilehash: 4ebb93d3ed325c115dcf311c821b014532dffc11
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663937"
---
# <a name="understanding-protection-level"></a>Koruma Düzeylerini Anlama

`ProtectionLevel` Özelliği bulunan birçok farklı sınıflarında gibi <xref:System.ServiceModel.ServiceContractAttribute> ve <xref:System.ServiceModel.OperationContractAttribute> sınıfları. Özellik, bir ileti bölümü (veya tam) nasıl korunduğunu denetler. Bu konuda, Windows Communication Foundation (WCF) özelliği ve nasıl çalıştığı açıklanmaktadır.

Koruma düzeyi ayarlama ile ilgili yönergeler için bkz: [nasıl yapılır: ProtectionLevel özelliğini ayarlama](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md).

> [!NOTE]
> Koruma düzeyleri yalnızca yapılandırmada yok, kod içinde ayarlayabilirsiniz.

## <a name="basics"></a>Temel bilgileri

Koruma düzeyi özelliğini daha iyi anlamak için aşağıdaki temel deyimleri geçerlidir:

- Herhangi bir ileti bölümü için üç temel koruma düzeyleri vardır. (Her yerde gerçekleşir) özelliği, birine ayarlanmış <xref:System.Net.Security.ProtectionLevel> sabit listesi değerleri. Koruma artan düzende içerirler:

  - `None`.

  - `Sign`. Korunan bölümün dijital olarak imzalanır. Bu, herhangi bir korumalı iletiyi bölümüyle değiştirme algılama sağlar.

  - `EncryptAndSign`. İleti bölümü, kapatmadan önce gizlilik emin olmak için şifrelenir.

- Yalnızca koruma gereksinimlerini ayarlayabilirsiniz *uygulama verileri* bu özellik. Örneğin, WS-Addressing üst bilgileri altyapı verilerdir ve bu nedenle, etkilenmez `ProtectionLevel`.

- Güvenlik modu ayarlandığında `Transport`, iletinin tamamı aktarım mekanizması tarafından korunur. Bu nedenle, bir iletinin farklı bölümleri için ayrı koruma düzeyini hiçbir etkisi olmaz.

- `ProtectionLevel` Geliştiricinin kurabileceği yoludur *en düşük düzey* bağlama ile uyumlu olmalıdır. Hizmet dağıtıldığında, yapılandırmada belirtilen gerçek bağlama olabilir veya en düşük düzey desteklemiyor olabilir. Örneğin, varsayılan <xref:System.ServiceModel.BasicHttpBinding> sınıfı (zaman etkinleştirilebilir rağmen) güvenlik sağlamaz. Bu nedenle, başka bir ayara sahip bir sözleşme ile kullanmaya `None` bir özel durum oluşturulmasına neden olur.

- Hizmet gerektiriyorsa en düşük `ProtectionLevel` için tüm iletileri `Sign`, (belki de bir WCF olmayan teknoloji tarafından oluşturulan) bir istemci şifrelemek ve tüm iletileri oturum (daha fazla gerekli en düşük olmayan). Bu durumda, WCF, istemci en fazla yapmış olduğundan, bir özel durum oluşturmayacaksa. Ancak, WCF uygulamaları (Hizmetleri veya istemciler) bir ileti bölümü mümkün olduğu durumlarda fazladan güvence altına almayacağını ancak en düşük düzeyi uyacaktır unutmayın. Kullanırken da unutmayın `Transport` daha ayrıntılı bir düzeyde korumak kendiliğinden alınamıyor, çünkü güvenlik modu olarak Aktarım ileti akışı aşırı güvenli.

- Ayarlarsanız `ProtectionLevel` açıkça ya da için `Sign` veya `EncryptAndSign`, güvenliği etkinleştirilmiş bir bağlama ardından kullanmanız gerekir ya da bir özel durum oluşturulur.

- Güvenlik sağlayan bir bağlamayı seçin ve ayarlamayın `ProtectionLevel` sözleşmesi, veriler şifrelenir ve imzalanmış tüm uygulama herhangi bir özellikte.

- Güvenlik etkin olmayan bir bağlama seçerseniz (örneğin, `BasicHttpBinding` sınıfında varsayılan olarak devre dışı güvenlik) ve `ProtectionLevel` hiçbir uygulama verileri korunur daha sonra açıkça, ayarlı değil.

- Tüm uygulama verileri, aktarım düzeyinde güvenlik uygulayan bir bağlama kullanıyorsanız, taşıma özelliklerine göre sağlanır.

- İleti düzeyi güvenlik uygulayan bir bağlama kullanırsanız, uygulama veri sözleşme ayarlamak koruma düzeylerine göre sağlanır. İletileri tüm uygulama verileri şifrelenir ve imzalı sonra bir koruma düzeyi belirtmezseniz.

- `ProtectionLevel` Farklı kapsam düzeylerinde ayarlanabilir. Yoktur, sonraki bölümde açıklanan kapsamlar ile ilişkilendirilmiş bir hiyerarşi.

## <a name="scoping"></a>Kapsam belirleme

Ayar `ProtectionLevel` üstteki API altındaki tüm düzeyleri düzeyini ayarlar. Varsa `ProtectionLevel` hiyerarşi düzeyi yepyeni bir düzeye artık sıfırlanır daha düşük bir düzeyde, aşağıdaki tüm API'leri için farklı bir değer ayarlanır (Bununla birlikte, API'ler, yukarıda yine de etkilenecek en üst düzey tarafından). Hiyerarşi aşağıdaki gibidir. Öznitelikleri aynı düzeyde eştir.

- <xref:System.ServiceModel.ServiceContractAttribute>

- <xref:System.ServiceModel.OperationContractAttribute>

- <xref:System.ServiceModel.FaultContractAttribute>

- <xref:System.ServiceModel.MessageContractAttribute>

- <xref:System.ServiceModel.MessageHeaderAttribute>

- <xref:System.ServiceModel.MessageBodyMemberAttribute>

## <a name="programming-protectionlevel"></a>ProtectionLevel programlama

Programa `ProtectionLevel` hiyerarşideki herhangi bir noktada özelliği için uygun değeri öznitelik uygularken ayarlamanız yeterlidir. Örnekler için bkz [nasıl yapılır: ProtectionLevel özelliğini ayarlama](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md).

> [!NOTE]
> Özelliği, hatalar ve ileti sözleşmeleri gerektiren bu özelliklerin nasıl çalıştığını anlamak ayarlanıyor. Daha fazla bilgi için [nasıl yapılır: ProtectionLevel özelliğini ayarlama](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md) ve [ileti anlaşmaları kullanma](../../../docs/framework/wcf/feature-details/using-message-contracts.md).

## <a name="ws-addressing-dependency"></a>WS-Addressing bağımlılık

Çoğu durumda, kullanarak [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) bir istemci oluşturmak için istemci ve hizmet sözleşmeleri aynı olmasını güvence altına alır. Ancak, görünüşte aynı sözleşme istemciye bir özel durum neden olabilir. Bu bağlama, WS-Addressing belirtimini desteklemiyor ve birden çok koruma düzeyi sözleşmesinde belirtilen olduğunda gerçekleşir. Örneğin, <xref:System.ServiceModel.BasicHttpBinding> sınıfı belirtimi desteklemiyor veya oluşturursanız, bağlama özel bir WS-Addressing desteklemez. `ProtectionLevel` Özelliği, farklı koruma düzeyleri tek sözleşmesindeki etkinleştirmek için WS-Addressing belirtimi dayanır. Bağlama WS-Addressing belirtimi desteklemiyorsa, tüm düzeyleri aynı koruma düzeyini ayarlanır. Sözleşmenin tüm kapsamlarda etkin bir koruma düzeyi sözleşmesinde kullanılan en güçlü koruma düzeyi için ayarlanır.

Bu ilk bakışta hata ayıklamak sabit bir sorunu neden olabilir. Birden fazla hizmeti yöntemlerini içeren bir istemci Sözleşmesi (bir arabirim) oluşturmak mümkündür. Diğer bir deyişle, aynı arabirimi birçok hizmet ile iletişim kuran istemci oluşturmak için kullanılır ve tek bir arabirim yöntemleri tüm hizmetleri içerir. Geliştirici nadir Bu senaryoda, belirli her hizmet için geçerli olan yöntemleri çağırmak için dikkatli olmalıdır. Bağlama <xref:System.ServiceModel.BasicHttpBinding> sınıfı, birden çok koruma düzeyleri olamaz desteklenir. Ancak, istemciye yanıtlama hizmet gerekli değerinden daha düşük bir koruma düzeyi ile istemciye yanıt verebilir. Bu durumda, daha yüksek bir koruma düzeyi beklediği istemci bir özel durum oluşturur.

Kod örneği, bu sorunu gösterir. Aşağıdaki örnek, bir hizmet ve istemci sözleşmesi gösterir. Bağlama olduğunu varsayın [ \<basicHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) öğesi. Bu nedenle, bir sözleşme üzerindeki tüm işlemler aynı koruma düzeyi var. Bu Tekdüzen koruma düzeyi arasında tüm işlemleri en fazla koruma düzeyi belirlenir.

Hizmet sözleşmesi şöyledir:

[!code-csharp[c_ProtectionLevel#7](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#7)]
[!code-vb[c_ProtectionLevel#7](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#7)]

Aşağıdaki kod, sözleşme arabirimi istemciye gösterir. Not içeren bir `Tax` farklı bir hizmet ile kullanılmak üzere tasarlanmıştır yöntemi:

[!code-csharp[c_ProtectionLevel#8](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#8)]
[!code-vb[c_ProtectionLevel#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#8)]

İstemci çağırdığında `Price` yöntemi, bir özel durum, hizmetten bir yanıt aldığında atar. İstemci belirttiğinde bu kaynaklanır bir `ProtectionLevel` üzerinde `ServiceContractAttribute`, ve bu nedenle varsayılan istemci kullanır (<xref:System.Net.Security.ProtectionLevel.EncryptAndSign>) dahil olmak üzere tüm yöntemleri için `Price` yöntemi. Ancak değerini kullanarak hizmeti döndürür <xref:System.Net.Security.ProtectionLevel.Sign> hizmet sözleşmesi ayarlamak, koruma düzeyi içeren tek bir yöntem tanımladığından düzey <xref:System.Net.Security.ProtectionLevel.Sign>. Bu durumda, istemci hizmetinden gelen yanıt doğrulanırken bir hata atar.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- <xref:System.ServiceModel.FaultContractAttribute>
- <xref:System.ServiceModel.MessageContractAttribute>
- <xref:System.ServiceModel.MessageHeaderAttribute>
- <xref:System.ServiceModel.MessageBodyMemberAttribute>
- <xref:System.Net.Security.ProtectionLevel>
- [Hizmetleri Güvenli Hale Getirme](../../../docs/framework/wcf/securing-services.md)
- [Nasıl yapılır: ProtectionLevel özelliğini ayarlama](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md)
- [Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
- [İleti Anlaşmaları Kullanma](../../../docs/framework/wcf/feature-details/using-message-contracts.md)
