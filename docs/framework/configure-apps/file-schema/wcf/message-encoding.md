---
title: İleti Kodlama
ms.date: 03/30/2017
ms.assetid: f30ee941-aca9-4c67-82a5-421568496f07
ms.openlocfilehash: 7fb0d4a994eaf1497841691eb76261329a48599d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59168759"
---
# <a name="message-encoding"></a>İleti Kodlama
Kodlama, Unicode karakter kümesini bir dizi bayta dönüştürme işlemidir. Kod çözme ters işlemidir. Windows Communication Foundation (WCF) için SOAP iletilerini kodlama üç türlerini içerir: Metin, ikili ve ileti aktarım en iyi duruma getirme mekanizması (MTOM).  
  
 `binaryMessageEncoding` Yapılandırma bölümü ikili tabanlı XML iletileri için kullanılan karakter kodlamasını ve ileti sürüm oluşturmayı belirtir. İkili ileti Kodlayıcısı Kablodaki ikili Windows Communication Foundation (WCF) iletilerini kodlayan. Bu kodlama ileti çok hızlı aktarımını sonuçları karşın, birlikte çalışabilirlik tabanlı WS - üzerinde * standartları kaybolur.  
  
 `mtomMessageEncoding` Yapılandırma bölümü bir ileti aktarım en iyi duruma getirme mekanizması (MTOM) kodlama kullanılarak bir ileti için kullanılan karakter kodlamasını ve ileti sürüm oluşturmayı belirtir. (MTOM), Windows Communication Foundation (WCF) iletilerinde ikili veri aktarımı için verimli bir teknolojidir. MTOM Kodlayıcısı, verimlilik ve birlikte çalışabilirlik arasında bir denge dener. MTOM kodlama çoğu XML metin biçiminde aktarır, ancak büyük ikili veri blokları olarak ileterek iyileştirir-olan metin dönüştürme olmadan.  
  
 `textMessageEncoding` Yapılandırma bölümü, kablo metin tabanlı iletileri oluşturmak için kullanılan bir metin Kodlayıcı belirtir. Bu Kodlayıcı tarafından üretilen iletileri, WS - için uygun * Interop bağlı. Web hizmeti veya Web hizmeti istemcisi, metinsel XML genellikle anlayabilirsiniz. Ancak, büyük ikili veri olarak metin blokları iletme XML iletileri kodlaması için az verimli yöntemdir  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)
- [Bağlamaları Genişletme](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Özel Bağlamalar](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [İleti Kodlayıcı Seçme](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)
