---
title: 'Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], creating custom bindings
ms.assetid: 203a9f9e-3a73-427c-87aa-721c56265b29
ms.openlocfilehash: da67d923b36d673c87c90ba79b72ad4e1fc64a0c
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988763"
---
# <a name="how-to-create-a-custom-binding-using-the-securitybindingelement"></a>Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma
Windows Communication Foundation (WCF), yapılandırılabilir, ancak WCF 'nin desteklediği tüm güvenlik seçeneklerini yapılandırırken tam esneklik sağlamayan, sistem tarafından sağlanan çeşitli bağlamaları içerir. Bu konu, bireysel bağlama öğelerinden doğrudan özel bir bağlamanın nasıl oluşturulduğunu ve böyle bir bağlama oluştururken belirtime bazı güvenlik ayarlarını vurgulabileceğinizi gösterir. Özel Bağlamalar Oluşturma hakkında daha fazla bilgi için bkz. [bağlamaları genişletme](../../../../docs/framework/wcf/extending/extending-bindings.md).  
  
> [!WARNING]
> <xref:System.ServiceModel.Channels.SecurityBindingElement>, olarak <xref:System.ServiceModel.Channels.IDuplexSessionChannel> <xref:System.ServiceModel.TransferMode> ayarlandığındaTCPaktarımıtarafındankullanılanvarsayılankanalşekliolan<xref:System.ServiceModel.TransferMode.Buffered>kanal şeklini desteklemez. Bu senaryoda kullanmak <xref:System.ServiceModel.TransferMode> <xref:System.ServiceModel.TransferMode.Streamed> için<xref:System.ServiceModel.Channels.SecurityBindingElement> ' i ayarlamanız gerekir.  
  
## <a name="creating-a-custom-binding"></a>Özel bağlama oluşturma  
 WCF 'de tüm bağlamalar *bağlama öğelerinden*oluşur. Her bağlama öğesi <xref:System.ServiceModel.Channels.BindingElement> sınıfından türetilir. Standart sistem tarafından sağlanmış bağlamalar için bağlama öğeleri sizin için oluşturulur ve yapılandırılır, ancak bazı özellik ayarlarını özelleştirebilirsiniz.  
  
 Buna karşılık, özel bir bağlama oluşturmak için bağlama öğeleri oluşturulup yapılandırılır ve <xref:System.ServiceModel.Channels.CustomBinding> bağlama öğelerinden oluşturulur.  
  
 Bunu yapmak için, tek tek bağlama öğelerini, <xref:System.ServiceModel.Channels.BindingElementCollection> sınıfının bir örneği tarafından temsil edilen bir koleksiyona ekler ve ardından bu nesneye `CustomBinding` eşit olan `Elements` özelliği ayarlayın. Bağlama öğelerini aşağıdaki sırayla eklemeniz gerekir: İşlem akışı, güvenilir oturum, güvenlik, bileşik çift yönlü, tek yönlü, akış güvenliği, Ileti kodlama ve taşıma. Her bağlamada listelenen tüm bağlama öğelerinin gerekli olduğunu unutmayın.  
  
## <a name="securitybindingelement"></a>SecurityBindingElement  
 Her biri <xref:System.ServiceModel.Channels.SecurityBindingElement> sınıfından türetilen ileti düzeyi güvenliği ile ilişkili üç bağlama öğesi. Üç <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>, ,ve.<xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> , <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> Karma mod güvenliği sağlamak için kullanılır. İleti katmanı güvenlik sağlıyorsa diğer iki öğe kullanılır.  
  
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
|`Message`|Http|SymmetricSecurityBindingElement|SymmetricSecurityBindingElement|SymmetricSecurityBindingElement (kimlik doğrulama modu = SecureConversation)|  
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
  
 SecurityBindingElements üzerinde birçok yapılandırılabilir ayar olduğunu unutmayın. Daha fazla bilgi için bkz. [SecurityBindingElement Kimlik doğrulama modları](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).  
  
 Daha fazla bilgi için bkz. [güvenli konuşmalar ve güvenli oturumlar](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md).  
  
## <a name="procedures"></a>Yordamlar  
  
#### <a name="to-create-a-custom-binding-that-uses-a-symmetricsecuritybindingelement"></a>SymmetricSecurityBindingElement kullanan özel bir bağlama oluşturmak için  
  
1. <xref:System.ServiceModel.Channels.BindingElementCollection> Adı`outputBec`ile sınıfın bir örneğini oluşturun.  
  
2. <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> Sınıfının bir örneğini döndüren `M:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationBindingElement(true)`static yöntemini çağırın.  
  
3. Sınıfınınyöntemini<xref:System.ServiceModel.Channels.BindingElement> çağırarak koleksiyona (`outputBec`) ekleyin. <xref:System.Collections.ObjectModel.Collection%601> `Add` <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
  
4. <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> Sınıfının bir örneğini oluşturun ve koleksiyona ekleyin (`outputBec`). Bu, bağlama tarafından kullanılan kodlamayı belirtir.  
  
5. Oluşturun ve koleksiyona ekleyin (`outputBec`). <xref:System.ServiceModel.Channels.HttpTransportBindingElement> Bu, bağlamanın HTTP taşımasını kullandığını belirtir.  
  
6. <xref:System.ServiceModel.Channels.CustomBinding> Sınıfın bir örneğini oluşturarak ve koleksiyonu `outputBec` oluşturucuya geçirerek yeni bir özel bağlama oluşturun.  
  
7. Elde edilen özel bağlama, standart <xref:System.ServiceModel.WSHttpBinding>ile aynı özelliklerin birçoğunu paylaşır. İleti düzeyinde güvenlik ve Windows kimlik bilgilerini belirtir, ancak güvenli oturumları devre dışı bırakır, hizmet kimlik bilgisinin bant dışı olarak belirtilmesini gerektirir ve imzaları şifrelemez. Son, yalnızca <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A> Özellik 4. adımda gösterildiği gibi ayarlanarak denetlenebilir. Diğer ikisi de standart bağlamasındaki ayarlar kullanılarak denetlenebilir.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek, kullanan özel bir bağlama oluşturmak için tamamen bir <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>işlev sağlar.  
  
### <a name="code"></a>Kod  
 [!code-csharp[c_CustomBinding#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#20)]
 [!code-vb[c_CustomBinding#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombinding/vb/source.vb#20)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.SecurityBindingElement>
- <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>
- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Bağlamaları Genişletme](../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Sistem Tarafından Sağlanan Bağlamalar](../../../../docs/framework/wcf/system-provided-bindings.md)
