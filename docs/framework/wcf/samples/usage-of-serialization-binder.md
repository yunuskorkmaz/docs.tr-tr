---
title: "Seri Hale Getirme Bağlayıcısı Kullanımı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ab46c087-200c-45bf-9c95-5a6cda6e8b98
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e35df7934ffb330feb45e5ff7167c9715f2d291e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="usage-of-serialization-binder"></a>Seri Hale Getirme Bağlayıcısı Kullanımı
Bu örnek nasıl kullanılacağını göstermektedir <xref:System.Runtime.Serialization.SerializationBinder> , serileştirildiğinde genel bir tür sürümünü değiştirmek için.  
  
## <a name="demonstrates"></a>Gösteriler  
 <xref:System.Runtime.Serialization.SerializationBinder>, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>  
  
## <a name="discussion"></a>Tartışma  
 Bu örnek, farklı sürümlerini hedefleyen nasıl iki varlık göstermektedir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ikili biçimlendirici ve seri hale getirme Bağlayıcısı kullanılarak iletişim kurabilir.  
  
 Bu örnek geliştirme gerçekleştirildi .NET uzaktan iletişim kullanma. Bir sunucu hedefleme, örnek oluşur [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], genel türler ve bir hedefleme iki farklı istemci ile bir sözleşme uygulayan [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)] ve başka bir hedefleme [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)].  
  
 Sunucu ekler bir <xref:System.Runtime.Serialization.SerializationBinder> türleri sürümünü değiştirmek için ikili biçimlendirici için uygun şekilde serileştirme üzerinde böylece her iki istemcinin çıkarabilen bu türlerde düzgün.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırma  
  
1.  İstemci yürütmek için SBGenericsVTS çözüme sağ tıklayın (6 projeleri) ve ardından **özellikleri**.  
  
2.  İçinde **ortak özellikleri**seçin **başlangıç projesi**seçeneğini belirleyip **birden fazla başlangıç projesi**.  
  
3.  Seçin **Server** ilk, ardından **Client20** ve ardından **Client40**. Seçin **Başlat** bu üç eylem projeleri ve ayarlamak rest bırakın **hiçbiri**.  
  
4.  Tıklatın **Tamam** örneği çalıştırmak için F5 tuşuna basın.
