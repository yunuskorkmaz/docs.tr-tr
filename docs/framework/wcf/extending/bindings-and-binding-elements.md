---
title: Bağlamalar ve Bağlama Öğeleri
ms.date: 03/30/2017
helpviewer_keywords:
- binding elements [WCF]
ms.assetid: 765ff77b-7682-4ea3-90eb-e4d751e37379
ms.openlocfilehash: eae78220196395ba3002141f01d554f2335a1f28
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64613355"
---
# <a name="bindings-and-binding-elements"></a>Bağlamalar ve Bağlama Öğeleri
Bağlamaları değil olarak adlandırılan özel yapılandırma öğelerinin koleksiyonları *bağlama öğelerinin*hizmet uç noktası çağrılamadığından veya hizmet çalışma zamanı tarafından bir istemci olduğunda değerlendirilir. Bir bağlama içinde bağlama öğelerin sırasını ve türünü, seçim ve uç noktanın kanal yığınında protokolü ve taşıma kanalları yığınlama sırasını belirler.  
  
 Bağlamaları, özellikle sistem tarafından sağlanan bağlamalar, genellikle en sık değiştirilen kapsüllenmiş bağlama öğeleri özelliklerini yansıtan yapılandırma özellikleri de vardır.  
  
 Bağlama, tam olarak bir aktarım bağlama öğesi içermelidir. Her aktarım bağlama öğesi, en fazla bir ileti bağlama öğesi bağlama için kodlama ekleyerek geçersiz kılınabilir bağlama öğesi, kodlama varsayılan bir ileti gösterir. Bağlama, aktarım ve bağlama öğeleri Kodlayıcı ek olarak, herhangi bir sayıda birlikte hizmet ve bir uç noktasından bir SOAP ileti göndermek için gereken işlevselliği uygulamak Protokolü bağlama öğeleri içerebilir. Ayrıntılar için bkz [hizmetlerini yapılandırın ve istemciler için bağlamaları kullanma](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).  
  
## <a name="extending-bindings-and-binding-elements"></a>Bağlamaları genişletme ve bağlama öğeleri  
 Windows Communication Foundation (WCF), çok çeşitli senaryoları kapsayan sistem tarafından sağlanan bağlamalar içerir. (Daha fazla bilgi için bkz: [System-Provided bağlamaları](../../../../docs/framework/wcf/system-provided-bindings.md).) Zamanlar olabilir, ancak WCF'de yer almayan bir bağlama oluşturun ve gerektiğinde. Aşağıdaki senaryolarda, yeni bir bağlama oluşturulmasını gerektirir.  
  
- Yeni bir bağlama öğesi (örneğin, bir yeni taşıma, kodlama veya protokolü bağlama öğesi) kullanmak için bu bağlama öğesi içeren yeni bir bağlama oluşturmanız gerekir. Örneğin, özel bir eklediyseniz `UdpTransportBindingElement` UDP taşıma için yapmak için yeni bir bağlama oluşturmanız gerekir kullanın. Kullanarak bu davranışı gerçekleştirme hakkında bilgi için <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> yazın, bkz: [özel bağlamalar](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
- Var olan bağlama öğeleri bir şekilde yapılandırmak için ortak özellik açığa çıkarmamak için sistem tarafından sağlanan bağlamalar. Örneğin, hangi imzalama ve şifreleme işlemleri gerçekleştirilir sırasını değiştirmek için yeni bir bağlama oluşturmanız gerekir. Bu davranış gerçekleştirme hakkında daha fazla bilgi için bkz: [nasıl yapılır: Sistem tarafından sağlanan bir bağlamayı özelleştirme](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).  
  
- Yalnızca belirli yapılandırma seçenekleri sunan Kurumsal standart bağlantıları kurmak için. Örneğin, şirketiniz için bir değişken oluşturmak için <xref:System.ServiceModel.WSHttpBinding> hangi güvenlik devre dışı bırakılamaz, şirketinizin gibi davranan bir yeni bağlama oluşturmasını <xref:System.ServiceModel.WSHttpBinding>, ancak her zaman açık güvenlik. Ayrıntılar için bkz [Creating User-Defined bağlamaları](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md).  
  
- Bazı özelleştirme meta verileri, genellikle gerçekleştirmek için ancak mutlaka yapılandırmak veya bazı özel bağlama öğesini kullanmak için. Bağlamalar ve bağlama öğeleri için meta veri desteği sağlama hakkında daha fazla bilgi için bkz. [yapılandırma ve meta veri desteği](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md).  

## <a name="channels-bindings-and-binding-elements"></a>Kanallar, bağlamalar ve bağlama öğeleri  
 Bağlamalar ve bağlama öğeleri öznitelikleri ve davranışlar içerir, uygulama programlama modelini fabrikaları ve dinleyiciler, ileti Kodlayıcı ve taşıma ve protokolü içerir kanal modeli arasında bağlantı olduğundan uygulamaları. Genellikle, bağlama öğeleri ve bağlamaları kanalları uygulama katmanı tarafından kullanılmak üzere etkinleştirmek için uygulanır.  
  
 Kanal katmanını devre dışı uygulamalı veya ileti alıp hizmet katmanından ve bu iletileri uç noktalar arasında taşır. Bir istemcide kanal katmanını, bir ağ uç noktası için kanal oluşturma kanal fabrikaları yığınıdır. Bir hizmette bir ağ uç noktada alınan kanalları kabul kanal dinleyicileri yığınını kanal katmanıdır.  
  
 İki genel tür kanal vardır: kanallar protokolünü ve taşıma kanalları. Taşıma kanalları başka bir ağ uç noktasından gerçek bir ileti aktarım için sorumludur. Taşıma kanalları varsayılan ileti Kodlayıcı olmalıdır ve bir ileti Kodlayıcı bağlama öğesi sağlanan bir diğer ileti Kodlayıcı kullanmanız mümkün olması gerekir. İleti Kodlayıcı için açma sorumlu olduğu bir <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType> hat gösterimine ve tersi. Protokol kanalını SOAP düzeyi protokolleri (örneğin, WS-güvenlik veya WS-ReliableMessaging) uygulamak için sorumlu olursunuz.  
  
 Taşıma ve protokol kanallar için birincil gereksinim, gerekli kanal arabirimleri uygulayan ' dir. Bunlar gerekir ilişkili fabrikaları ve dinleyiciler, çalışma kanal katmanı oluşturan ve benzeri. WCF gerekir ilişkili bağlama öğeleri olarak gelen kanal uygulamaları kullanmak için türetilen <xref:System.ServiceModel.Channels.BindingElement> her kanal için ilgili bağlama uzantı öğesi türetileneklenmeküzereyapılandırmadosyalarınaolmalıdır<xref:System.ServiceModel.Configuration.BindingElementExtensionElement>.  
  
 İleti Kodlayıcı, protokol ve aktarım için belirtilen önceki, bağlayıcı öğeleri olarak kanal uygulamaları bir kanal yığını oluşturmak için yığın olabilir ve bir sıralı kümesine hizalamak için bağlama mekanizmadır. Bağlamalar ve bağlama öğeleri uygulama programlama modeli kanal modeline bağlanın. Koddan, kanal uygulamaları doğrudan kullanabilirsiniz, ancak bağlama öğeleri olarak kodlayıcılar aktarımları ve protokolleri uygulanmazsa hizmet katmanı programlama modelinden kullanılamaz.  
  
 Kanallar ve bağlama öğeleri geliştirme hakkında daha fazla ayrıntı için bkz. [kanal katmanını genişletme](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md).
