---
title: İleti Kodlama
ms.date: 03/30/2017
ms.assetid: f30ee941-aca9-4c67-82a5-421568496f07
ms.openlocfilehash: 8e5a71095ba62e0e2e6592c8b7b83b67602ef7e7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931594"
---
# <a name="message-encoding"></a>İleti Kodlama
Kodlama, Unicode karakter kümesini bir bayt dizisine dönüştürme işlemidir. Kod çözme işlemi ters işlemdir. Windows Communication Foundation (WCF), SOAP iletileri için üç tür kodlama içerir: Metin, Ikili ve Ileti Iletimi Iyileştirme mekanizması (MTOM).  
  
 `binaryMessageEncoding` Yapılandırma bölümü, ikili tabanlı xml iletileri için kullanılan karakter kodlamasını ve ileti sürüm oluşturmayı belirtir. İkili ileti Kodlayıcısı, Windows Communication Foundation (WCF) iletilerini kablo üzerinde ikili olarak kodlar. Bu kodlama, iletilerin çok hızlı aktarılmasına neden olsa da, WS-* standartlarına dayalı olarak birlikte çalışabilirlik kaybedilir.  
  
 `mtomMessageEncoding` Yapılandırma bölümü, ileti iletimi iyileştirme mekanizması (MTOM) kodlaması kullanan bir ileti için kullanılan karakter kodlamasını ve ileti sürüm oluşturmayı belirtir. (MTOM), ikili verileri Windows Communication Foundation (WCF) iletilerinde iletmek için verimli bir teknolojidir. MTOM Kodlayıcısı verimlilik ve birlikte çalışabilirlik arasında bir denge kurmaya çalışır. MTOM kodlaması çoğu XML 'i metinsel biçimde iletir, ancak bu verileri,, metne dönüştürülmeksizin olduğu gibi ileterek büyük ikili veri bloklarını iyileştirir.  
  
 `textMessageEncoding` Yapılandırma bölümü, tel üzerinde metin tabanlı iletiler oluşturmak için kullanılan bir metin Kodlayıcısı belirtir. Bu kodlayıcı tarafından üretilen iletiler WS-* tabanlı birlikte çalışma için uygundur. Web hizmeti veya Web hizmeti istemcisi, genellikle metinsel XML 'i anlayabilir. Bununla birlikte, büyük ikili veri bloklarını metin olarak iletme, XML iletilerini kodlamada en düşük verimli yöntemdir  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- [Bağlamalar](../../../wcf/bindings.md)
- [Bağlamaları Genişletme](../../../wcf/extending/extending-bindings.md)
- [Özel Bağlamalar](../../../wcf/extending/custom-bindings.md)
- [\<customBinding >](custombinding.md)
- [İleti Kodlayıcı Seçme](../../../wcf/feature-details/choosing-a-message-encoder.md)
