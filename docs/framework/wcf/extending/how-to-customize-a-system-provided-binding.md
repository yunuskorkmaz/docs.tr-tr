---
title: 'Nasıl yapılır: Sistem Tarafından Sağlanan Bir Bağlamayı Özelleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f8b97862-e8bb-470d-8b96-07733c21fe26
ms.openlocfilehash: 6b92382b4a37168c33f9e97077ad292d27ea5bc3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797016"
---
# <a name="how-to-customize-a-system-provided-binding"></a>Nasıl yapılır: Sistem Tarafından Sağlanan Bir Bağlamayı Özelleştirme
Windows Communication Foundation (WCF), temel bağlama öğelerinin bazı özelliklerini yapılandırmanıza imkan tanıyan, ancak özelliklerin tümünü değil, sistem tarafından sunulan birçok bağlama içerir. Bu konu başlığı altında, bağlama öğelerinde nasıl özel bir bağlama oluşturacağınız özelliklerinin nasıl ayarlanacağı gösterilmektedir.  
  
 Bağlama öğelerinin sistem tarafından sağlanmış bağlamaları kullanılmadan doğrudan oluşturulması ve yapılandırılması hakkında daha fazla bilgi için bkz. [Özel Bağlamalar](custom-bindings.md).  
  
 Özel Bağlamalar Oluşturma ve genişletme hakkında daha fazla bilgi için bkz. [bağlamaları genişletme](extending-bindings.md).  
  
 WCF 'de tüm bağlamalar *bağlama öğelerinden*oluşur. Her bağlama öğesi <xref:System.ServiceModel.Channels.BindingElement> sınıfından türetilir. Kendi bağlama öğelerini <xref:System.ServiceModel.BasicHttpBinding> oluşturma ve yapılandırma gibi sistem tarafından sağlanmış bağlamalar. Bu konu başlığı altında, bağlama üzerinde doğrudan gösterilmeyen bu bağlama öğelerinin özelliklerine erişme ve değiştirme işlemlerinin nasıl yapılacağı gösterilmektedir. Özellikle, <xref:System.ServiceModel.BasicHttpBinding> sınıfı.  
  
 Bireysel bağlama öğeleri, <xref:System.ServiceModel.Channels.BindingElementCollection> sınıfı tarafından temsil edilen bir koleksiyonda bulunur ve bu sırayla eklenir: İşlem akışı, güvenilir oturum, güvenlik, bileşik çift yönlü, tek yönlü, akış güvenliği, Ileti kodlama ve taşıma. Her bağlamada listelenen tüm bağlama öğelerinin gerekli olduğunu unutmayın. Kullanıcı tanımlı bağlama öğeleri, bu bağlama öğesi koleksiyonunda de görünebilir ve daha önce açıklanan sırada görünmelidir. Örneğin, Kullanıcı tanımlı bir taşımanın bağlama öğesi koleksiyonunun son öğesi olması gerekir.  
  
 <xref:System.ServiceModel.BasicHttpBinding> Sınıfı üç bağlama öğesi içerir:  
  
1. Bir isteğe bağlı güvenlik bağlama öğesi, <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> HTTP taşıması (ileti düzeyi güvenliği) <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> veya Aktarım katmanı güvenlik sağlar, bu durumda https aktarımının kullanıldığı durumlarda kullanılan sınıfı.  
  
2. Ya da <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> veya <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>için gerekli bir ileti Kodlayıcısı bağlama öğesi.  
  
3. Gerekli bir taşıma bağlama öğesi <xref:System.ServiceModel.Channels.HttpTransportBindingElement> <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>, ya da.  
  
 Bu örnekte, bağlamanın bir örneğini oluşturur, bundan *özel bir bağlama* oluşturur, özel bağlamadaki bağlama öğelerini inceler ve http bağlama öğesini bulduğumuz, `KeepAliveEnabled` özelliğini olarak `false`ayarlayacağız. Özelliği doğrudan üzerinde gösterilmez, bu nedenle bağlama öğesine gitmek ve bu özelliği ayarlamak için özel bir bağlama oluşturuyoruz. `BasicHttpBinding` `KeepAliveEnabled`  
  
### <a name="to-modify-a-system-provided-binding"></a>Sistem tarafından sağlanmış bir bağlamayı değiştirmek için  
  
1. <xref:System.ServiceModel.BasicHttpBinding> Sınıfının bir örneğini oluşturun ve güvenlik modunu ileti düzeyi olarak ayarlayın.  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#1)]
     [!code-vb[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#1)]  
  
2. Bağlamadan özel bir bağlama oluşturun ve özel bağlamanın özelliklerinden <xref:System.ServiceModel.Channels.BindingElementCollection> birinden bir sınıf oluşturun.  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#2)]
     [!code-vb[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#2)]  
  
3. Sınıfından döngü yapın ve <xref:System.ServiceModel.Channels.HttpTransportBindingElement> sınıfını bulduğunuzda <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> özelliğini olarak `false`ayarlayın. <xref:System.ServiceModel.Channels.BindingElementCollection>  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#3)]
     [!code-vb[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Özel Bağlamalar](custom-bindings.md)
