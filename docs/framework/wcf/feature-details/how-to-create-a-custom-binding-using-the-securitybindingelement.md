---
title: 'Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], creating custom bindings
ms.assetid: 203a9f9e-3a73-427c-87aa-721c56265b29
ms.openlocfilehash: df40d8dbd5af9acf9e9484ee7694df2bba7ad9f1
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50181140"
---
# <a name="how-to-create-a-custom-binding-using-the-securitybindingelement"></a>Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma
Windows Communication Foundation (WCF) yapılandırılabilir, ancak tam esneklik sağlamaz, WCF destekleyen tüm güvenlik seçeneklerini yapılandırırken birçok sistem tarafından sağlanan bağlamalar içerir. Bu konu, tek tek bağlama öğelerini doğrudan özel bağlama oluşturma işlemini gösterir ve böyle bir bağlamanın oluştururken belirttiğiniz güvenlik ayarlarından bazıları vurgular. Özel bağlamalar oluşturma hakkında daha fazla bilgi için bkz. [bağlamaları genişletme](../../../../docs/framework/wcf/extending/extending-bindings.md).  
  
> [!WARNING]
>  <xref:System.ServiceModel.Channels.SecurityBindingElement> desteklemediği <xref:System.ServiceModel.Channels.IDuplexSessionChannel> kanal TCP ile varsayılan kanal şekli kullanım şekli ne zaman aktarım <xref:System.ServiceModel.TransferMode> ayarlanır <xref:System.ServiceModel.TransferMode.Buffered>. Ayarlamalısınız <xref:System.ServiceModel.TransferMode> için <xref:System.ServiceModel.TransferMode.Streamed> kullanmak için <xref:System.ServiceModel.Channels.SecurityBindingElement> Bu senaryoda.  
  
## <a name="creating-a-custom-binding"></a>Özel bağlama oluşturma  
 WCF'de tüm bağlamaları, oluşur *bağlama öğelerinin*. Her bağlama öğesi türetildiği <xref:System.ServiceModel.Channels.BindingElement> sınıfı. Standart sistem tarafından sağlanan bağlamaları için bağlama öğeleri oluşturulur ve bazı özellik ayarları özelleştirebilirsiniz ancak sizin için yapılandırılmış.  
  
 Buna karşılık, özel bir bağlama oluşturmak için bağlama öğeleri oluşturulup yapılandırıldıktan ve <xref:System.ServiceModel.Channels.CustomBinding> bağlama öğelerini oluşturulur.  
  
 Bunu yapmak için tek tek bağlama öğelerinin bir örneği tarafından temsil edilen bir koleksiyon eklediğiniz <xref:System.ServiceModel.Channels.BindingElementCollection> sınıfı ve ardından `Elements` özelliği `CustomBinding` bu nesneye eşit. Bağlama öğeleri şu sırayla eklemeniz gerekir: işlem akışı, güvenilir oturum, güvenlik, çift yönlü bileşik, tek yönlü, Stream güvenlik, ileti kodlama ve taşıma. Listelenen tüm bağlama öğelerini her bağlamanın gerekli olduğunu unutmayın.  
  
## <a name="securitybindingelement"></a>SecurityBindingElement  
 Üç bağlama öğeleri ile ilgili tüm türetilen ileti düzeyi güvenliği için <xref:System.ServiceModel.Channels.SecurityBindingElement> sınıfı. Üç olan <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>, <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>, ve <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>. <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> Karma mod güvenliği sağlamak için kullanılır. Güvenlik iletisi katmanı sağlar, diğer iki öğe kullanılır.  
  
 Ek sınıflar, taşıma düzeyi güvenliği sağlandığında kullanılır:  
  
-   <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
-   <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
## <a name="required-binding-elements"></a>Bağlama öğelerinin gerekli  
 Çok sayıda içine bir bağlama birleştirilebilir olası bağlama öğeleri vardır. Bu birleşim geçerli değildir. Bu bölümde, bir güvenlik bağlama bulunması gereken gerekli öğeler açıklanmaktadır.  
  
 Geçerli güvenlik bağlamaları, aşağıdakiler dahil olmak üzere birçok faktöre bağlıdır:  
  
-   Güvenlik modu.  
  
-   Aktarım Protokolü.  
  
-   Sözleşmede belirtilen ileti değişim deseni (MEP).  
  
 Aşağıdaki tabloda her bir önceki faktörler bileşimi geçerli bağlama öğesi yığın yapılandırmalarını gösterir. Bunların en az gereksinimleri olduğunu unutmayın. İleti bağlama öğeleri, işlem bağlama öğeleri ve diğer bağlama öğeleri kodlama gibi bağlamaya ek bağlama öğeleri ekleyebilirsiniz.  
  
|Güvenlik modu|Taşıma|Sözleşme ileti değişim deseni|Sözleşme ileti değişim deseni|Sözleşme ileti değişim deseni|  
|-------------------|---------------|---------------------------------------|---------------------------------------|---------------------------------------|  
|||`Datagram`|`Request Reply`|`Duplex`|  
|Taşıma|HTTPS||||  
|||OneWayBindingElement|||  
|||HttpsTransportBindingElement|HttpsTransportBindingElement||  
||TCP||||  
|||OneWayBindingElement|||  
|||SSL veya Windows StreamSecurityBindingElement öğesini|SSL veya Windows StreamSecurityBindingElement öğesini|SSL veya Windows StreamSecurityBindingElement öğesini|  
|||TcpTransportBindingElement|TcpTransportBindingElement|TcpTransportBindingElement|  
|İleti|http|SymmetricSecurityBindingElement|SymmetricSecurityBindingElement|SymmetricSecurityBindingElement (kimlik doğrulama modu SecureConversation =)|  
|||||CompositeDuplexBindingElement|  
|||OneWayBindingElement||OneWayBindingElement|  
|||HttpTransportBindingElement|HttpTransportBindingElement|HttpTransportBindingElement|  
||TCP|SecurityBindingElement|SecurityBindingElement|SymmetricSecurityBindingElement (kimlik doğrulama modu SecureConversation =)|  
|||TcpTransportBindingElement|TcpTransportBindingElement|TcpTransportBindingElement|  
|Karışık (ileti kimlik bilgileri ile taşıma)|HTTPS|TransportSecurityBindingElement|TransportSecurityBindingElement||  
|||OneWayBindingElement|||  
|||HttpsTransportBindingElement|HttpsTransportBindingElement||  
||TCP|TransportSecurityBindingElement|SymmetricSecurityBindingElement (kimlik doğrulama modu SecureConversation =)|SymmetricSecurityBindingElement (kimlik doğrulama modu SecureConversation =)|  
|||OneWayBindingElement|||  
|||SSL veya Windows StreamSecurityBindingElement öğesini|SSL veya Windows StreamSecurityBindingElement öğesini|SSL veya Windows StreamSecurityBindingElement öğesini|  
|||TcpTransportBindingElement|TcpTransportBindingElement|TcpTransportBindingElement|  
  
 Birçok yapılandırılabilir ayarları SecurityBindingElements olduğunu unutmayın. Daha fazla bilgi için [SecurityBindingElement kimlik doğrulama modları](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).  
  
 Daha fazla bilgi için [güvenli konuşmaları ve oturumları güvenli](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md).  
  
## <a name="procedures"></a>Yordamlar  
  
#### <a name="to-create-a-custom-binding-that-uses-a-symmetricsecuritybindingelement"></a>SymmetricSecurityBindingElement kullanan özel bağlama oluşturma  
  
1.  Bir örneğini oluşturmak <xref:System.ServiceModel.Channels.BindingElementCollection> sınıfı adıyla `outputBec`.  
  
2.  Statik metodunu çağırın `M:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationBindingElement(true)`, örneğini döndüren <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> sınıfı.  
  
3.  Ekleme <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> koleksiyona (`outputBec`) çağırarak `Add` yöntemi <xref:System.Collections.ObjectModel.Collection%601> , <xref:System.ServiceModel.Channels.BindingElement> sınıfı.  
  
4.  Bir örneğini oluşturmak <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> sınıfı ve koleksiyona eklemek (`outputBec`). Bu bağlama tarafından kullanılan kodlamayı belirtir.  
  
5.  Oluşturma bir <xref:System.ServiceModel.Channels.HttpTransportBindingElement> ve koleksiyona eklemek (`outputBec`). Bu, bağlama HTTP aktarımı kullandığını belirtir.  
  
6.  Bir örneğini oluşturarak yeni özel bağlama oluşturma <xref:System.ServiceModel.Channels.CustomBinding> sınıfı ve koleksiyonu geçirme `outputBec` Oluşturucusu.  
  
7.  Sonuçta elde edilen özel bağlama birçok standart olarak aynı özellikleri paylaşır <xref:System.ServiceModel.WSHttpBinding>. Bu ileti düzeyi güvenliği ve Windows kimlik bilgilerini belirtir, ancak güvenli oturumlarını devre dışı bırakır, belirtilen-bant, hizmet kimlik bilgisi gerektirir ve imzalar şifrelemez. Yalnızca ayarlayarak son denetlenebilir <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A> adım 4'te gösterildiği gibi özelliği. Diğer iki standart bağlama üzerinde ayarları kullanılarak denetlenebilir.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek, kullanan özel bir bağlama oluşturmak için tam bir işlev sağlar. bir <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.  
  
### <a name="code"></a>Kod  
 [!code-csharp[c_CustomBinding#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#20)]
 [!code-vb[c_CustomBinding#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombinding/vb/source.vb#20)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>  
 <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Bağlamaları Genişletme](../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Sistem Tarafından Sağlanan Bağlamalar](../../../../docs/framework/wcf/system-provided-bindings.md)
