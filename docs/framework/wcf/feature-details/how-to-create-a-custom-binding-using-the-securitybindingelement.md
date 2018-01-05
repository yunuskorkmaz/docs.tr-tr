---
title: "Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: security [WCF], creating custom bindings
ms.assetid: 203a9f9e-3a73-427c-87aa-721c56265b29
caps.latest.revision: "19"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: e230c02d53f8222034dfd79872cde9c540c31963
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-custom-binding-using-the-securitybindingelement"></a>Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]yapılandırılabilir, ancak tüm güvenlik yapılandırma seçenekleri, tam esneklik sağlıyor mu birkaç sistem tarafından sağlanan bağlamaları içerir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] destekler. Bu konuda doğrudan tek tek bağlama öğelerini özel bağlama oluşturma gösterir ve bu tür bir bağlama oluşturulurken belirtilen güvenlik ayarlarını bazılarını vurgular. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]özel bağlama oluşturma, bkz: [bağlamaları genişletme](../../../../docs/framework/wcf/extending/extending-bindings.md).  
  
> [!WARNING]
>  <xref:System.ServiceModel.Channels.SecurityBindingElement>desteklemediği <xref:System.ServiceModel.Channels.IDuplexSessionChannel> kanal TCP tarafından varsayılan kanal şekli kullanımı şekli ne zaman aktarım <xref:System.ServiceModel.TransferMode> ayarlanır <xref:System.ServiceModel.TransferMode.Buffered>. Ayarlamalısınız <xref:System.ServiceModel.TransferMode> için <xref:System.ServiceModel.TransferMode.Streamed> kullanmak için <xref:System.ServiceModel.Channels.SecurityBindingElement> Bu senaryoda.  
  
## <a name="creating-a-custom-binding"></a>Özel bağlama oluşturma  
 İçinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tüm bağlamaları, oluşur *bağlama öğeleri*. Her bağlama öğesi türetilen <xref:System.ServiceModel.Channels.BindingElement> sınıfı. Standart sistem tarafından sağlanan bağlamaları için bağlama öğeleri oluşturulur ve bazı özellik ayarları özelleştirebilirsiniz olsa da, sizin için yapılandırılmış.  
  
 Buna karşılık, özel bağlama oluşturma için bağlama öğeleri oluşturulup yapılandırılıncaya ve <xref:System.ServiceModel.Channels.CustomBinding> bağlama öğelerini oluşturulur.  
  
 Bunu yapmak için tek tek bağlama öğelerinin bir örneği tarafından temsil edilen bir koleksiyon eklediğiniz <xref:System.ServiceModel.Channels.BindingElementCollection> sınıfı ve ardından `Elements` özelliği `CustomBinding` , bu nesneye eşit. Bağlama öğeleri aşağıdaki sırayla eklemeniz gerekir: işlem akış, güvenilir oturum, güvenlik, bileşik çift yönlü, tek yönlü, akış güvenliği, ileti kodlama ve taşıma. Listelenen tüm bağlama öğeleri her bağlama gerekli olduğunu unutmayın.  
  
## <a name="securitybindingelement"></a>SecurityBindingElement  
 Üç bağlama öğeleri arasında ilişki bunların tümü türetilen ileti düzeyi güvenlik için <xref:System.ServiceModel.Channels.SecurityBindingElement> sınıfı. Üç olan <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>, <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>, ve <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>. <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> Karma mod güvenliği sağlamak için kullanılır. İleti katmanı güvenlik sağlar, diğer iki öğe kullanılır.  
  
 Aktarım düzeyi güvenlik sağlandığında ek sınıfları kullanılır:  
  
-   <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
-   <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
## <a name="required-binding-elements"></a>Bağlama öğeleri gerekli  
 Çok sayıda içinde bir bağlaması birleştirilebilir olası bağlama öğeleri vardır. Bu kombinasyon geçerli değildir. Bu bölümde bir güvenlik bağlaması bulunmalıdır gerekli öğeleri açıklar.  
  
 Geçerli güvenlik bağlamaları aşağıdakiler gibi birçok faktöre bağlıdır:  
  
-   Güvenlik modu.  
  
-   Aktarım Protokolü.  
  
-   Sözleşmede belirtilen ileti değişim deseni (MEP).  
  
 Aşağıdaki tabloda her önceki Etkenler birleşimi için geçerli bağlama öğesi yığını yapılandırmaları gösterilmiştir. Bunlar gereken en düşük gereksinimleri olduğunu unutmayın. Bağlama öğeleri, işlem bağlama öğeleri ve diğer bağlama öğeleri kodlama ileti gibi bağlama ek bağlama öğeleri ekleyebilirsiniz.  
  
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
|Karma (ileti kimlik bilgileri ile aktarma)|HTTPS|TransportSecurityBindingElement|TransportSecurityBindingElement||  
|||OneWayBindingElement|||  
|||HttpsTransportBindingElement|HttpsTransportBindingElement||  
||TCP|TransportSecurityBindingElement|SymmetricSecurityBindingElement (kimlik doğrulama modu SecureConversation =)|SymmetricSecurityBindingElement (kimlik doğrulama modu SecureConversation =)|  
|||OneWayBindingElement|||  
|||SSL veya Windows StreamSecurityBindingElement öğesini|SSL veya Windows StreamSecurityBindingElement öğesini|SSL veya Windows StreamSecurityBindingElement öğesini|  
|||TcpTransportBindingElement|TcpTransportBindingElement|TcpTransportBindingElement|  
  
 SecurityBindingElements üzerinde birçok yapılandırılabilir ayarlar olduğunu unutmayın. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][SecurityBindingElement kimlik doğrulama modları](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Güvenli görüşmeleri ve güvenli oturumlar](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md).  
  
## <a name="procedures"></a>Yordamlar  
  
#### <a name="to-create-a-custom-binding-that-uses-a-symmetricsecuritybindingelement"></a>SymmetricSecurityBindingElement kullanan özel bağlama oluşturma  
  
1.  Bir örneğini oluşturmak <xref:System.ServiceModel.Channels.BindingElementCollection> sınıfı adı ile `outputBec`.  
  
2.  Statik metodunu çağırın `M:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationBindingElement(true)`, bir örneğini döndürür <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> sınıfı.  
  
3.  Ekleme <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> koleksiyonuna (`outputBec`) çağırarak `Add` yöntemi <xref:System.Collections.ObjectModel.Collection%601> , <xref:System.ServiceModel.Channels.BindingElement> sınıfı.  
  
4.  Bir örneğini oluşturmak <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> sınıfı ve koleksiyona eklemek (`outputBec`). Bu bağlama tarafından kullanılan kodlamayı belirtir.  
  
5.  Oluşturma bir <xref:System.ServiceModel.Channels.HttpTransportBindingElement> ve koleksiyona eklemek (`outputBec`). Bu bağlama HTTP aktarımı kullandığını belirtir.  
  
6.  Bir örneğini oluşturarak yeni özel bağlama oluşturma <xref:System.ServiceModel.Channels.CustomBinding> sınıfı ve koleksiyon geçirme `outputBec` Oluşturucusu.  
  
7.  Sonuçta elde edilen özel bağlama, standart olarak aynı özellikleri paylaşır <xref:System.ServiceModel.WSHttpBinding>. Bu ileti düzeyi güvenlik ve Windows kimlik bilgilerini belirtir ancak güvenli oturumlar devre dışı bırakır, belirtilen-bant, hizmet kimlik bilgilerini gerektirir ve imzalar şifrelemez. Son yalnızca ayarlayarak denetlenebilir <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A> adım 4'te gösterildiği gibi özelliği. Diğer iki standart bağlamada ayarları kullanılarak denetlenebilir.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek kullanan özel bağlama oluşturma için tam bir işlev sağlar bir <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.  
  
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
