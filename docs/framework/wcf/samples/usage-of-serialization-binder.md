---
description: 'Hakkında daha fazla bilgi edinin: serileştirme cildin kullanımı'
title: Seri Hale Getirme Bağlayıcısı Kullanımı
ms.date: 03/30/2017
ms.assetid: ab46c087-200c-45bf-9c95-5a6cda6e8b98
ms.openlocfilehash: ee00d8049ae644525f8013801dc7c453b9ad5aeb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798179"
---
# <a name="usage-of-serialization-binder"></a>Seri Hale Getirme Bağlayıcısı Kullanımı

Bu örnek, <xref:System.Runtime.Serialization.SerializationBinder> serileştirildiğinde genel bir türün sürümünü değiştirmek için öğesinin nasıl kullanılacağını gösterir.  
  
## <a name="demonstrates"></a>Gösteriler  

 <xref:System.Runtime.Serialization.SerializationBinder>, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>  
  
## <a name="discussion"></a>Tartışma  

 Bu örnek, .NET Framework farklı sürümlerini hedefleyen iki varlığın ikili biçimlendirici ve serileştirme cildi kullanarak nasıl iletişim kurabildiğini gösterir.  
  
Bu örnek .NET uzaktan Iletişim kullanılarak geliştirilmiştir. Bu, genel türler içeren bir sözleşme uygulayan .NET Framework 4 ve iki farklı istemci, bir hedef .NET Framework 2,0 ve başka bir hedefleme .NET Framework 4 ' ü hedefleyen bir sunucudan oluşur.  
  
 Sunucu, <xref:System.Runtime.Serialization.SerializationBinder> her iki istemci de bu türleri düzgün bir şekilde seri durumdan çıkarabilmesi için, bir ikili biçimlendirici öğesine bir ekler.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Bunu ayarlamak için örneği oluşturun ve çalıştırın  
  
1. İstemcisini yürütmek için, SBGenericsVTS (6 proje) çözümüne sağ tıklayın ve ardından **Özellikler**' i seçin.  
  
2. **Ortak özellikler**' de **Başlangıç projesi**' ni seçin ve **birden çok başlangıç** projesi ' ni seçin.  
  
3. Önce **sunucu** ' yı, ardından **Client20** ve ardından **Client40**' yi seçin. Bu üç proje için **Başlat** eylemini seçin ve REST öğesini **none** olarak bırakın.  
  
4. **Tamam** ' a tıklayın ve ardından örneği çalıştırmak için F5 ' e basın.
