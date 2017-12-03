---
title: "Bağlamalar ve Bağlama Öğeleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: binding elements [WCF]
ms.assetid: 765ff77b-7682-4ea3-90eb-e4d751e37379
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 39615c7a74d30ebd5f316988704992b49982c4a4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="bindings-and-binding-elements"></a>Bağlamalar ve Bağlama Öğeleri
Bağlamaları olan koleksiyonları adlı özel bir yapılandırma öğelerinin *bağlama öğeleri*, hizmet çalışma zamanı tarafından bir istemci her değerlendirilir veya hizmet uç noktası oluşturulur. İçinde bir bağlaması bağlama öğelerin sırasını ve türünü, seçim ve bir uç noktanın kanal yığınında protokolü ve taşıma kanalları yığınlama sırasını belirler.  
  
 Bağlamaları, özellikle sistem tarafından sağlanan bağlamalar, genellikle kapsüllenmiş bağlama öğeleri en sık değiştirilen özelliklerini yansıtan yapılandırma özellikleri de vardır.  
  
 Bir bağlama tam olarak bir aktarım bağlama öğesi içermelidir. Her aktarım bağlama öğesi, en çok bir ileti bağlama öğesi bağlama için kodlama ekleyerek kılınabilir bağlama öğesi kodlama varsayılan bir ileti gösterir. Taşıma ve Kodlayıcı bağlama öğeleri ek olarak, bağlama herhangi bir sayıda birlikte hizmet ve bir uç noktasından bir SOAP iletisi göndermek için gerekli işlevselliği uygulamak Protokolü bağlama öğeleri içerebilir. Ayrıntılar için bkz [kullanarak bağlamaları yapılandırma hizmetler ve istemcileri için](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).  
  
## <a name="extending-bindings-and-binding-elements"></a>Bağlamaları genişletme ve bağlama öğeleri  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]kadar çeşitli senaryoları kapak sistem tarafından sağlanan bağlamaları içerir. (Daha fazla bilgi için bkz: [System-Provided bağlamaları](../../../../docs/framework/wcf/system-provided-bindings.md).) Oluşturma ve kullanma dahil değilse bir bağlama gerektiğinde zamanlar olabilir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Aşağıdaki senaryolar, yeni bir bağlama oluşturulmasını gerektirir.  
  
-   Yeni bir bağlama öğesi (örneğin, bir yeni taşıma, kodlama veya protokolü bağlama öğesi) kullanmak için bu bağlama öğesini içeren yeni bir bağlama oluşturmanız gerekir. Örneğin, özel bir eklediyseniz `UdpTransportBindingElement` UDP taşıma için yapmak için yeni bir bağlama oluşturmanız gerekecek bunu kullanın. Bu davranış kullanarak gerçekleştirme hakkında bilgi için <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> yazın, bkz: [özel bağlamaları](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
-   Var olan bağlama öğeleri bir şekilde yapılandırmak için ortak özellikleri kullanıma sunmak değil için sistem tarafından sağlanan bağlamalar. Örneğin, hangi imzalama ve şifreleme işlemleri gerçekleştirilir sırasını değiştirmek için yeni bir bağlama oluşturmanız gerekir. Bu davranış gerçekleştirme hakkında daha fazla bilgi için bkz: [nasıl yapılır: bağlama System-Provided özelleştirme](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).  
  
-   Yalnızca belirli yapılandırma seçenekleri kullanıma şirket standart bağlantıları kurmak için. Örneğin, şirketiniz için bir değişken oluşturmak için <xref:System.ServiceModel.WSHttpBinding> hangi güvenlik devre dışı bırakılamaz, şirketinizin oluşturmak için gibi davranır yeni bir bağlama <xref:System.ServiceModel.WSHttpBinding>, ancak güvenlik her zaman açık. Ayrıntılar için bkz [Creating User-Defined bağlamaları](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md).  
  
-   Bazı özelleştirme meta verileri, genellikle gerçekleştirmek için ancak mutlaka yapılandırmak veya bazı özel bağlama öğesini kullanan için. Bağlamalar ve bağlama öğeleri meta verileri desteği sağlama hakkında daha fazla bilgi için bkz: [yapılandırma ve meta verileri desteği](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md).  
  
-  
  
## <a name="channels-bindings-and-binding-elements"></a>Kanallar, bağlamalar ve bağlama öğeleri  
 Bağlamalar ve bağlama öğeleri öznitelikleri ve davranışları içerir, uygulama programlama modeli ve oluşturucuları dinleyicileri, ileti kodlayıcılar ve taşıma ve protokolü içerir kanal modeli arasındaki bağlantıyı olan uygulamaları. Genellikle, bağlama öğeleri ve bağlamaları kanalları uygulama katmanı tarafından kullanılmak üzere etkinleştirmek için uygulanır.  
  
 Kanal katmanını kapalı aktarır veya ve hizmet katmanından iletilerini alır ve bu iletileri uç noktalar arasında taşımaları. Bir istemcide bir ağ uç noktası için Kanallar oluşturma kanal fabrikaları yığınını kanal katmanıdır. Bir hizmette ağ uç noktada alınan kanalları kabul kanal dinleyicileri yığınını kanal katmanıdır.  
  
 Kanallar iki genel tür vardır: kanallar protokolünü ve taşıma kanalları. Taşıma kanalları başka bir ağ uç noktasından bir ileti gerçek aktarım için sorumludur. Taşıma kanalları varsayılan ileti Kodlayıcı olmalıdır ve bir ileti Kodlayıcı bağlama öğesi sağlanan bir alternatif ileti Kodlayıcı kullanmanız mümkün olması gerekir. İleti Kodlayıcı için dönüş sorumlu olduğu bir <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType> hat gösterimine ve tam tersini. Protokol kanalını SOAP düzeyi protokolleri (örneğin, WS-güvenlik veya WS-ReliableMessaging) uygulamak için sorumlu.  
  
 Birincil aktarım ve protokolü kanallar için gerekli kanal arabirimleri uyguladıkları gereksinimdir. Bunlar gerekir ilişkili oluşturucular ve dinleyicileri, bir çalışma kanal katman oluşturmak için ve benzeri. Gelen kanal uygulamalarının kullanımına [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gerekir türetilmiş bir ilişkili bağlama öğeleri olacak şekilde <xref:System.ServiceModel.Channels.BindingElement> her kanal için ve türetilen yapılandırma dosyalarını içine eklenmek üzere ilgili bağlama uzantı öğesi olması gerekir <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>.  
  
 İleti kodlayıcılar, protokol ve aktarım için belirtilen önceki, bağlayıcı öğeleri olarak kanal uygulamaları bir kanal yığını form Yığılmış olabilir ve bir sıralanmış küme hizalamak için bağlama mekanizmadır. Bağlamalar ve bağlama öğeleri uygulama programlama modeli kanal modeli bağlayın. Koddan, kanal uygulamaları doğrudan kullanabilirsiniz, ancak bağlama öğeleri olarak kodlayıcılar, aktarımları ve protokolleri uygulanması sürece hizmet katmanı programlama modeli kullanılamaz.  
  
 Kanallar ve bağlama öğeleri geliştirme hakkında daha fazla bilgi için bkz: [kanal katmanını genişletme](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md).
