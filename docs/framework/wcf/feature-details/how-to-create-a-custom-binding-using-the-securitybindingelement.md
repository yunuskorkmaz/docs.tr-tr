---
title: 'Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], creating custom bindings
ms.assetid: 203a9f9e-3a73-427c-87aa-721c56265b29
ms.openlocfilehash: 15fdd50b05bd2217cb9819373cd1c015da52b15b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599015"
---
# <a name="how-to-create-a-custom-binding-using-the-securitybindingelement"></a>Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma
Windows Communication Foundation (WCF), yapılandırılabilir, ancak WCF 'nin desteklediği tüm güvenlik seçeneklerini yapılandırırken tam esneklik sağlamayan, sistem tarafından sağlanan çeşitli bağlamaları içerir. Bu konu, bireysel bağlama öğelerinden doğrudan özel bir bağlamanın nasıl oluşturulduğunu ve böyle bir bağlama oluştururken belirtime bazı güvenlik ayarlarını vurgulabileceğinizi gösterir. Özel Bağlamalar Oluşturma hakkında daha fazla bilgi için bkz. [bağlamaları genişletme](../extending/extending-bindings.md).  
  
> [!WARNING]
> <xref:System.ServiceModel.Channels.SecurityBindingElement>, <xref:System.ServiceModel.Channels.IDuplexSessionChannel> olarak AYARLANDıĞıNDA TCP aktarımı tarafından kullanılan varsayılan kanal şekli olan kanal şeklini desteklemez <xref:System.ServiceModel.TransferMode> <xref:System.ServiceModel.TransferMode.Buffered> . <xref:System.ServiceModel.TransferMode> <xref:System.ServiceModel.TransferMode.Streamed> Bu senaryoda kullanmak için ' i ayarlamanız gerekir <xref:System.ServiceModel.Channels.SecurityBindingElement> .  
  
## <a name="creating-a-custom-binding"></a>Özel bağlama oluşturma  
 WCF 'de tüm bağlamalar *bağlama öğelerinden*oluşur. Her bağlama öğesi <xref:System.ServiceModel.Channels.BindingElement> sınıfından türetilir. Standart sistem tarafından sağlanmış bağlamalar için bağlama öğeleri sizin için oluşturulur ve yapılandırılır, ancak bazı özellik ayarlarını özelleştirebilirsiniz.  
  
 Buna karşılık, özel bir bağlama oluşturmak için bağlama öğeleri oluşturulup yapılandırılır ve <xref:System.ServiceModel.Channels.CustomBinding> bağlama öğelerinden oluşturulur.  
  
 Bunu yapmak için, tek tek bağlama öğelerini, sınıfının bir örneği tarafından temsil edilen bir koleksiyona ekler <xref:System.ServiceModel.Channels.BindingElementCollection> ve ardından `Elements` `CustomBinding` Bu nesneye eşit olan özelliği ayarlayın. Bağlama öğelerini şu sırayla eklemeniz gerekir: Işlem akışı, güvenilir oturum, güvenlik, bileşik çift yönlü, tek yönlü, akış güvenliği, Ileti kodlama ve taşıma. Her bağlamada listelenen tüm bağlama öğelerinin gerekli olduğunu unutmayın.  
  
## <a name="securitybindingelement"></a>SecurityBindingElement  
 Her biri sınıfından türetilen ileti düzeyi güvenliği ile ilişkili üç bağlama öğesi <xref:System.ServiceModel.Channels.SecurityBindingElement> . Üç,, <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> ve <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> . , <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> Karma mod güvenliği sağlamak için kullanılır. İleti katmanı güvenlik sağlıyorsa diğer iki öğe kullanılır.  
  
 Aktarım düzeyi güvenliği sağlandığında ek sınıflar kullanılır:  
  
- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
## <a name="required-binding-elements"></a>Gerekli bağlama öğeleri  
 Bir bağlamada birleştirilebilecek çok sayıda olası bağlama öğesi vardır. Bu kombinasyonlar geçerli değildir. Bu bölümde, bir güvenlik bağlamasında bulunması gereken öğeler açıklanmaktadır.  
  
 Geçerli güvenlik bağlamaları, aşağıdakiler de dahil olmak üzere birçok etkene bağımlıdır:  
  
- Güvenlik modu.  
  
- Aktarım Protokolü.  
  
- Sözleşmede belirtilen ileti değişim biçimi (MEP).  
  
 Aşağıdaki tabloda, önceki faktörlerin her birleşimi için geçerli bağlama öğesi yığın konfigürasyonları gösterilmektedir. Bunların en düşük gereksinimleri olduğunu unutmayın. Bağlamada ileti kodlama bağlama öğeleri, işlem bağlama öğeleri ve diğer bağlama öğeleri gibi ek bağlama öğeleri ekleyebilirsiniz.  
  
|Güvenlik modu|Aktarım|Sözleşme Iletisi değişim kriteri|Sözleşme Iletisi değişim kriteri|Sözleşme Iletisi değişim kriteri|  
|-------------------|---------------|---------------------------------------|---------------------------------------|---------------------------------------|  
|||`Datagram`|`Request Reply`|`Duplex`|  
|Aktarım|'Dir||||  
|||OneWayBindingElement|||  
|||HttpsTransportBindingElement|HttpsTransportBindingElement||  
||TCP||||  
|||OneWayBindingElement|||  
|||SSL veya Windows StreamSecurityBindingElement|SSL veya Windows StreamSecurityBindingElement|SSL veya Windows StreamSecurityBindingElement|  
|||TcpTransportBindingElement|TcpTransportBindingElement|TcpTransportBindingElement|  
|İleti|Http|SymmetricSecurityBindingElement|SymmetricSecurityBindingElement|SymmetricSecurityBindingElement (kimlik doğrulama modu = SecureConversation)|  
|||||CompositeDuplexBindingElement|  
|||OneWayBindingElement||OneWayBindingElement|  
|||HttpTransportBindingElement|HttpTransportBindingElement|HttpTransportBindingElement|  
||TCP|SecurityBindingElement|SecurityBindingElement|SymmetricSecurityBindingElement (kimlik doğrulama modu = SecureConversation)|  
|||TcpTransportBindingElement|TcpTransportBindingElement|TcpTransportBindingElement|  
|Karma (ileti kimlik bilgileriyle taşıma)|'Dir|TransportSecurityBindingElement|TransportSecurityBindingElement||  
|||OneWayBindingElement|||  
|||HttpsTransportBindingElement|HttpsTransportBindingElement||  
||TCP|TransportSecurityBindingElement|SymmetricSecurityBindingElement (kimlik doğrulama modu = SecureConversation)|SymmetricSecurityBindingElement (kimlik doğrulama modu = SecureConversation)|  
|||OneWayBindingElement|||  
|||SSL veya Windows StreamSecurityBindingElement|SSL veya Windows StreamSecurityBindingElement|SSL veya Windows StreamSecurityBindingElement|  
|||TcpTransportBindingElement|TcpTransportBindingElement|TcpTransportBindingElement|  
  
 SecurityBindingElements üzerinde birçok yapılandırılabilir ayar olduğunu unutmayın. Daha fazla bilgi için bkz. [SecurityBindingElement Kimlik doğrulama modları](securitybindingelement-authentication-modes.md).  
  
 Daha fazla bilgi için bkz. [güvenli konuşmalar ve güvenli oturumlar](secure-conversations-and-secure-sessions.md).  
  
## <a name="procedures"></a>Yordamlar  
  
#### <a name="to-create-a-custom-binding-that-uses-a-symmetricsecuritybindingelement"></a>SymmetricSecurityBindingElement kullanan özel bir bağlama oluşturmak için  
  
1. <xref:System.ServiceModel.Channels.BindingElementCollection>Adı ile sınıfın bir örneğini oluşturun `outputBec` .  
  
2. `M:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationBindingElement(true)`Sınıfının bir örneğini döndüren static yöntemini çağırın <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> .  
  
3. <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> `outputBec` Sınıfının yöntemini çağırarak koleksiyona () ekleyin `Add` <xref:System.Collections.ObjectModel.Collection%601> <xref:System.ServiceModel.Channels.BindingElement> .  
  
4. Sınıfının bir örneğini oluşturun <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> ve koleksiyona ekleyin ( `outputBec` ). Bu, bağlama tarafından kullanılan kodlamayı belirtir.  
  
5. Oluşturun <xref:System.ServiceModel.Channels.HttpTransportBindingElement> ve koleksiyona ekleyin ( `outputBec` ). Bu, bağlamanın HTTP taşımasını kullandığını belirtir.  
  
6. Sınıfın bir örneğini oluşturarak <xref:System.ServiceModel.Channels.CustomBinding> ve koleksiyonu oluşturucuya geçirerek yeni bir özel bağlama oluşturun `outputBec` .  
  
7. Elde edilen özel bağlama, standart ile aynı özelliklerin birçoğunu paylaşır <xref:System.ServiceModel.WSHttpBinding> . İleti düzeyinde güvenlik ve Windows kimlik bilgilerini belirtir, ancak güvenli oturumları devre dışı bırakır, hizmet kimlik bilgisinin bant dışı olarak belirtilmesini gerektirir ve imzaları şifrelemez. Son, yalnızca <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A> özellik 4. adımda gösterildiği gibi ayarlanarak denetlenebilir. Diğer ikisi de standart bağlamasındaki ayarlar kullanılarak denetlenebilir.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek, kullanan özel bir bağlama oluşturmak için tamamen bir işlev sağlar <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> .  
  
### <a name="code"></a>Kod  
 [!code-csharp[c_CustomBinding#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#20)]
 [!code-vb[c_CustomBinding#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombinding/vb/source.vb#20)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.SecurityBindingElement>
- <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>
- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Bağlamaları Genişletme](../extending/extending-bindings.md)
- [Sistem tarafından sağlanmış bağlamalar](../system-provided-bindings.md)
