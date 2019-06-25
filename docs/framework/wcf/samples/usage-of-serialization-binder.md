---
title: Seri Hale Getirme Bağlayıcısı Kullanımı
ms.date: 03/30/2017
ms.assetid: ab46c087-200c-45bf-9c95-5a6cda6e8b98
ms.openlocfilehash: 10900950b935b484053fe8e37263f0dfc25eba99
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2019
ms.locfileid: "67348452"
---
# <a name="usage-of-serialization-binder"></a>Seri Hale Getirme Bağlayıcısı Kullanımı
Bu örnek nasıl kullanılacağını gösterir <xref:System.Runtime.Serialization.SerializationBinder> , serileştirilmiş olduğunda, genel bir türün sürümü değiştirmek için.  
  
## <a name="demonstrates"></a>Gösteriler  
 <xref:System.Runtime.Serialization.SerializationBinder>, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>  
  
## <a name="discussion"></a>Tartışma  
 Bu örnek, olan .NET Framework can farklı sürümlerini hedefleme iletişim kurmasını ikili biçimlendirici serileştirme Bağlayıcısı ile nasıl iki varlık gösterir.  
  
Bu örnek, .NET uzaktan iletişim kullanarak geliştirilmiştir. Bir sunucu hedefleme oluşur [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], genel türler ve iki farklı istemciler, bir hedefleme .NET Framework 2.0 ve başka bir hedefleyen bir sözleşme uygulayan [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)].  
  
 Sunucu ekler bir <xref:System.Runtime.Serialization.SerializationBinder> türleri sürümünü değiştirmek için ikili biçimlendirici için uygun şekilde seri hale getirme üzerinde bu nedenle her iki istemcinin seri durumdan çıkarabilen türlerine düzgün.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1. İstemci yürütmek için SBGenericsVTS çözüme sağ tıklayın (6 projeler) ve ardından **özellikleri**.  
  
2. İçinde **ortak özellikler**seçin **başlangıç projesi**, ardından **birden fazla başlangıç projesi**.  
  
3. Seçin **sunucu** ilk, ardından **Client20** ardından **Client40**. Seçin **Başlat** bu üç eylem projeleri ve ayarlamak geri kalan bırakın **hiçbiri**.  
  
4. Tıklayın **Tamam** ve örneği çalıştırmak için F5 tuşuna basın.
