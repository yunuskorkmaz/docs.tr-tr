---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: System-Provided bağlamayı özelleştirme'
title: 'Nasıl yapılır: Sistem Tarafından Sağlanan Bir Bağlamayı Özelleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f8b97862-e8bb-470d-8b96-07733c21fe26
ms.openlocfilehash: c0463a8e427e6503f0e68bc58eb488f9b0bad15a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668961"
---
# <a name="how-to-customize-a-system-provided-binding"></a>Nasıl yapılır: Sistem Tarafından Sağlanan Bir Bağlamayı Özelleştirme

Windows Communication Foundation (WCF), temel bağlama öğelerinin bazı özelliklerini yapılandırmanıza imkan tanıyan, ancak özelliklerin tümünü değil, sistem tarafından sunulan birçok bağlama içerir. Bu konu başlığı altında, bağlama öğelerinde nasıl özel bir bağlama oluşturacağınız özelliklerinin nasıl ayarlanacağı gösterilmektedir.  
  
 Bağlama öğelerinin sistem tarafından sağlanmış bağlamaları kullanılmadan doğrudan oluşturulması ve yapılandırılması hakkında daha fazla bilgi için bkz. [Özel Bağlamalar](custom-bindings.md).  
  
 Özel Bağlamalar Oluşturma ve genişletme hakkında daha fazla bilgi için bkz. [bağlamaları genişletme](extending-bindings.md).  
  
 WCF 'de tüm bağlamalar *bağlama öğelerinden* oluşur. Her bağlama öğesi <xref:System.ServiceModel.Channels.BindingElement> sınıfından türetilir. <xref:System.ServiceModel.BasicHttpBinding>Kendi bağlama öğelerini oluşturma ve yapılandırma gibi sistem tarafından sağlanmış bağlamalar. Bu konu başlığı altında, bağlama üzerinde doğrudan gösterilmeyen bu bağlama öğelerinin özelliklerine erişme ve değiştirme işlemlerinin nasıl yapılacağı gösterilmektedir. Özellikle, <xref:System.ServiceModel.BasicHttpBinding> sınıfı.  
  
 Tek tek bağlama öğeleri, sınıfı tarafından temsil edilen bir koleksiyonda bulunur <xref:System.ServiceModel.Channels.BindingElementCollection> ve şu sıraya eklenir: Işlem akışı, güvenilir oturum, güvenlik, bileşik çift yönlü, tek yönlü, akış güvenliği, Ileti kodlama ve taşıma. Her bağlamada listelenen tüm bağlama öğelerinin gerekli olduğunu unutmayın. Kullanıcı tanımlı bağlama öğeleri, bu bağlama öğesi koleksiyonunda de görünebilir ve daha önce açıklanan sırada görünmelidir. Örneğin, Kullanıcı tanımlı bir taşımanın bağlama öğesi koleksiyonunun son öğesi olması gerekir.  
  
 <xref:System.ServiceModel.BasicHttpBinding>Sınıfı üç bağlama öğesi içerir:  
  
1. Bir isteğe bağlı güvenlik bağlama öğesi, <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> http taşıması (ileti düzeyi güvenliği) veya <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> Aktarım katmanı güvenlik sağlar, bu durumda https aktarımının kullanıldığı durumlarda kullanılan sınıfı.  
  
2. Ya da veya için gerekli bir ileti Kodlayıcısı bağlama öğesi <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> .  
  
3. Gerekli bir taşıma bağlama öğesi, ya da <xref:System.ServiceModel.Channels.HttpTransportBindingElement> <xref:System.ServiceModel.Channels.HttpsTransportBindingElement> .  
  
 Bu örnekte, bağlamanın bir örneğini oluşturur, bundan *özel bir bağlama* oluşturur, özel bağlamadaki bağlama öğelerini INCELER ve http bağlama öğesini bulduğumuz, `KeepAliveEnabled` özelliğini olarak ayarlayacağız `false` . `KeepAliveEnabled`Özelliği doğrudan üzerinde gösterilmez `BasicHttpBinding` , bu nedenle bağlama öğesine gitmek ve bu özelliği ayarlamak için özel bir bağlama oluşturuyoruz.  
  
### <a name="to-modify-a-system-provided-binding"></a>Sistem tarafından sağlanmış bir bağlamayı değiştirmek için  
  
1. Sınıfının bir örneğini oluşturun <xref:System.ServiceModel.BasicHttpBinding> ve güvenlik modunu ileti düzeyi olarak ayarlayın.  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#1)]
     [!code-vb[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#1)]  
  
2. Bağlamadan özel bir bağlama oluşturun ve <xref:System.ServiceModel.Channels.BindingElementCollection> özel bağlamanın özelliklerinden birinden bir sınıf oluşturun.  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#2)]
     [!code-vb[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#2)]  
  
3. <xref:System.ServiceModel.Channels.BindingElementCollection>Sınıfından döngü yapın ve <xref:System.ServiceModel.Channels.HttpTransportBindingElement> sınıfını bulduğunuzda <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> özelliğini olarak ayarlayın `false` .  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#3)]
     [!code-vb[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Özel Bağlamalar](custom-bindings.md)
