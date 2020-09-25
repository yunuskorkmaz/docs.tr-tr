---
title: İleti Kodlama
ms.date: 03/30/2017
ms.assetid: f30ee941-aca9-4c67-82a5-421568496f07
ms.openlocfilehash: 018cbc778627fc429e443fc590fa4c0f52d2a68a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204885"
---
# <a name="message-encoding"></a>İleti Kodlama

Kodlama, Unicode karakter kümesini bir bayt dizisine dönüştürme işlemidir. Kod çözme işlemi ters işlemdir. Windows Communication Foundation (WCF), SOAP iletileri için üç tür kodlama içerir: metin, Ikili ve Ileti Iletimi Iyileştirme mekanizması (MTOM).  
  
 `binaryMessageEncoding`Yapılandırma bölümü, ikili tabanlı xml iletileri için kullanılan karakter kodlamasını ve ileti sürüm oluşturmayı belirtir. İkili ileti Kodlayıcısı, Windows Communication Foundation (WCF) iletilerini kablo üzerinde ikili olarak kodlar. Bu kodlama, iletilerin çok hızlı aktarılmasına neden olsa da, WS-* standartlarına dayalı olarak birlikte çalışabilirlik kaybedilir.  
  
 `mtomMessageEncoding`Yapılandırma bölümü, Ileti Iletimi Iyileştirme mekanizması (MTOM) kodlaması kullanan bir ileti için kullanılan karakter kodlamasını ve ileti sürüm oluşturmayı belirtir. (MTOM), ikili verileri Windows Communication Foundation (WCF) iletilerinde iletmek için verimli bir teknolojidir. MTOM Kodlayıcısı verimlilik ve birlikte çalışabilirlik arasında bir denge kurmaya çalışır. MTOM kodlaması çoğu XML 'i metinsel biçimde iletir, ancak bu verileri,, metne dönüştürülmeksizin olduğu gibi ileterek büyük ikili veri bloklarını iyileştirir.  
  
 `textMessageEncoding`Yapılandırma bölümü, tel üzerinde metin tabanlı iletiler oluşturmak için kullanılan bir metin Kodlayıcısı belirtir. Bu kodlayıcı tarafından üretilen iletiler WS-* tabanlı birlikte çalışma için uygundur. Web hizmeti veya Web hizmeti istemcisi, genellikle metinsel XML 'i anlayabilir. Bununla birlikte, büyük ikili veri bloklarını metin olarak iletme, XML iletilerini kodlamada en düşük verimli yöntemdir  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- [Bağlamalar](../../../wcf/bindings.md)
- [Bağlamaları Genişletme](../../../wcf/extending/extending-bindings.md)
- [Özel Bağlamalar](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [İleti Kodlayıcı Seçme](../../../wcf/feature-details/choosing-a-message-encoder.md)
