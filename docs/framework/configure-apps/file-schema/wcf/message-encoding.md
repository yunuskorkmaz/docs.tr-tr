---
title: "İleti Kodlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f30ee941-aca9-4c67-82a5-421568496f07
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b3040a16b6d167c4f066b2ddbd0a542741f88d62
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="message-encoding"></a>İleti Kodlama
Kodlama Unicode karakter kümesini bir bayt dizisi dönüştürme işlemidir. Kod çözme ters bir işlemdir. Windows Communication Foundation (WCF) SOAP iletiler için kodlamayı üç türleri içerir: metin ve ikili ileti iletim en iyi duruma getirme mekanizmasını (MTOM).  
  
 `binaryMessageEncoding` Yapılandırma bölümü ikili tabanlı XML iletileri için kullanılan karakter kodlama ve ileti sürüm belirtir. İkili ileti Kodlayıcı ikili hat üzerinde Windows Communication Foundation (WCF) iletilerinde kodlar. Bu kodlama ileti çok hızlı aktarımını sonuçları, birlikte çalışabilirlik tabanlı WS - üzerinde * standartları kaybolur.  
  
 `mtomMessageEncoding` Yapılandırma bölümünde bir ileti iletim en iyi duruma getirme mekanizmasını (MTOM) kodlama kullanılarak bir ileti için kullanılan karakter kodlama ve ileti sürüm belirtir. (MTOM), Windows Communication Foundation (WCF) iletilerindeki ikili veri iletmek için verimli bir teknolojidir. MTOM Kodlayıcısı verimliliği ve birlikte çalışabilirlik arasında bir denge dener. MTOM kodlama çoğu XML metin biçiminde aktarır ancak bunları olarak ileterek büyük ikili veri blokları en iyi duruma getirir-metne dönüştürme olmadan, ise.  
  
 `textMessageEncoding` Yapılandırma bölümü kablo metin tabanlı iletileri oluşturmak için kullanılan bir metin Kodlayıcı belirtir. Bu Kodlayıcı tarafından üretilen iletileri WS - için uygun * birlikte çalışabilirliği tabanlı. Genellikle Web hizmeti veya Web hizmeti istemcisi metinsel XML anlayabilirsiniz. Ancak, büyük metin olarak ikili veri blokları iletmek için XML iletileri kodlama az verimli yöntemdir  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)  
 [Bağlamaları Genişletme](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Özel Bağlamalar](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [İleti Kodlayıcı Seçme](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)
