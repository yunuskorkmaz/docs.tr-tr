---
title: Bağlamalar ve Bağlama Öğeleri
ms.date: 03/30/2017
helpviewer_keywords:
- binding elements [WCF]
ms.assetid: 765ff77b-7682-4ea3-90eb-e4d751e37379
ms.openlocfilehash: d4d69495c1ae19b6799fdb9981f6b332cc2580d3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795855"
---
# <a name="bindings-and-binding-elements"></a>Bağlamalar ve Bağlama Öğeleri
Bağlamalar, istemci veya hizmet uç noktası oluşturulduğunda hizmet çalışma zamanı tarafından değerlendirilen *bağlama öğeleri*olarak adlandırılan özel yapılandırma öğelerinin koleksiyonlarıdır. Bir bağlama içindeki bağlama öğelerinin türü ve sırası, bir uç noktanın kanal yığınındaki protokol ve taşıma kanallarının seçim ve yığınlama sırasını belirler.  
  
 Özellikle sistem tarafından sağlanmış bağlamaların bağlamaları, genellikle kapsüllenmiş bağlama öğelerinin en sık değiştirilen özelliklerini yansıtan bir dizi yapılandırma özelliği de vardır.  
  
 Bağlama tam olarak bir aktarım bağlama öğesi içermelidir. Her bir aktarım bağlama öğesi, bağlamaya en çok bir ileti kodlama bağlama öğesi eklenerek geçersiz kılınabilen varsayılan bir ileti kodlama bağlama öğesi anlamına gelir. Aktarım ve kodlayıcı bağlama öğelerine ek olarak bağlama, bir bir uç noktadan diğerine bir SOAP iletisi göndermek ve göndermek için gereken işlevleri birlikte uygulayan herhangi bir sayıda protokol bağlama öğesi içerebilir. Ayrıntılar için bkz. [Hizmetleri ve Istemcileri yapılandırmak Için bağlamaları kullanma](../using-bindings-to-configure-services-and-clients.md).  
  
## <a name="extending-bindings-and-binding-elements"></a>Bağlamaları ve bağlama öğelerini genişletme  
 Windows Communication Foundation (WCF), çok çeşitli senaryoları kapsayan sistem tarafından sağlanmış bağlamaları içerir. (Daha fazla bilgi için bkz. [sistem tarafından sunulan bağlamalar](../system-provided-bindings.md).) Ancak, WCF 'ye dahil olmayan bir bağlama oluşturmanız ve kullanmanız gerektiği zamanlar olabilir. Aşağıdaki senaryolar yeni bir bağlamanın oluşturulmasını gerektirir.  
  
- Yeni bir bağlama öğesi (örneğin, yeni bir aktarım, kodlama veya protokol bağlama öğesi) kullanmak için, o bağlama öğesini içeren yeni bir bağlama oluşturmanız gerekir. Örneğin, UDP taşıması için özel `UdpTransportBindingElement` bir eklediyseniz, bunu kullanmak için yeni bir bağlama oluşturmanız gerekir. Bu davranışı <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> türünü kullanarak gerçekleştirme hakkında daha fazla bilgi için bkz. [Özel Bağlamalar](custom-bindings.md).  
  
- Mevcut bağlama öğelerini, sistem tarafından belirtilen bağlamaların ortak özelliklerde kullanıma sunulmayan bir şekilde yapılandırmak için. Örneğin, imzalama ve şifreleme işlemlerinin gerçekleştirildiği sırayı değiştirmek için yeni bir bağlama oluşturmanız gerekir. Bu davranışı gerçekleştirme hakkında daha fazla bilgi için [bkz. nasıl yapılır: Sistem tarafından sağlanmış bağlamayı](how-to-customize-a-system-provided-binding.md)özelleştirin.  
  
- Yalnızca belirli yapılandırma seçeneklerini sunan kurumsal standart bağlamalar oluşturmak için. Örneğin, şirketiniz için güvenliği devre dışı bırakılabileceği bir değişken <xref:System.ServiceModel.WSHttpBinding> oluşturmak için, <xref:System.ServiceModel.WSHttpBinding>gibi davranan, ancak güvenliği her zaman açık olan yeni bir bağlama oluşturun. Ayrıntılar için bkz. [Kullanıcı Tanımlı Bağlamalar Oluşturma](creating-user-defined-bindings.md).  
  
- Genellikle meta verilerin özelleştirilmesini gerçekleştirmek için, ancak bazı özel bağlama öğelerini yapılandırmak veya kullanmak zorunda değildir. Bağlama ve bağlama öğelerine meta veri desteği sağlama hakkında daha fazla bilgi için bkz. [yapılandırma ve meta veri desteği](configuration-and-metadata-support.md).  

## <a name="channels-bindings-and-binding-elements"></a>Kanallar, bağlamalar ve bağlama öğeleri  
 Bağlamalar ve bağlama öğeleri, öznitelikleri ve davranışları içeren uygulama programlama modeli ile fabrika ve dinleyicileri, ileti kodlayıcıları ve taşıma ve protokol dahil olduğu kanal modelini içeren bağlantıdır uygulamalarını. Genellikle, uygulama katmanı tarafından kullanılacak kanalları etkinleştirmek için bağlama öğeleri ve bağlamaları uygulanır.  
  
 Kanal katmanı kapalı veya hizmet katmanına ileti alır ve bu iletileri uç noktalar arasında aktarır. Bir istemcide Kanal katmanı, bir ağ uç noktasına kanal oluşturan Kanal fabrikası yığınıdır. Bir hizmette kanal katmanı, bir ağ uç noktasında alınan kanalları kabul eden bir kanal dinleyicileri yığınıdır.  
  
 İki genel kanal türü vardır: Protokol kanalları ve aktarım kanalları. Aktarım kanalları bir ağ uç noktasından diğerine gerçek bir ileti aktarımından sorumludur. Taşıma kanalları varsayılan bir ileti Kodlayıcısı olmalıdır ve bir ileti Kodlayıcısı bağlama öğesi aracılığıyla sağlanan alternatif bir ileti Kodlayıcısı kullanabilmelidir. İleti Kodlayıcısı, bir <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType> hat gösterimine veya bunun tersini yapmaktan sorumludur. Protokol kanalları, SOAP düzeyi protokolleri (örneğin, WS-Security veya WS-ReliableMessaging) uygulamaktan sorumludur.  
  
 Taşıma ve protokol kanalları için birincil gereksinim, gerekli kanal arabirimlerini uygulamalarıdır. Çalışan bir kanal katmanı oluşturmak için, ilişkili fabrika ve dinleyicilerine sahip olmaları gerekir ve bu şekilde devam eder. WCF 'den kanal uygulamalarını kullanmak için her kanal için ' den <xref:System.ServiceModel.Channels.BindingElement> türetilmiş ilişkili bağlama öğeleri olması gerekir ve öğesinden <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>türetilenyapılandırmadosyalarınaeklenmeküzereilgilibağlamauzantıöğesiolmalıdır.  
  
 Daha önce bahsedildiği gibi, ileti kodlayıcıları, protokol ve taşıma kanalı uygulamalarına yönelik bağlama öğeleri bir kanal yığını oluşturmak için ayrılabilir ve bunları sıralı bir küme içine hizalamak için bir mekanizma bağlamadır. Bağlamalar ve bağlama öğeleri, uygulama programlama modelini kanal modeline bağlar. Doğrudan koddan kanal uygulamalarınızı kullanabilirsiniz, ancak kodlayıcılar, aktarımlar ve protokoller, hizmet katmanı programlama modelinden kullanılamayan bağlama öğeleri olarak uygulanamazlar.  
  
 Kanalları ve bağlama öğelerini geliştirme hakkında ayrıntılar için bkz. [Kanal Katmanını Genişletme](extending-the-channel-layer.md).
