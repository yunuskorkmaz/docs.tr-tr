---
title: '#pragma checksum - C# Referans'
ms.date: 07/20/2015
f1_keywords:
- '#pragma checksum'
helpviewer_keywords:
- '#pragma checksum [C#]'
ms.assetid: 3673e4ca-6098-4ec1-890f-8fceb2a794a2
ms.openlocfilehash: 1bbb404e1183daa5e68e512e7439b6ae52abd605
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712487"
---
# <a name="pragma-checksum-c-reference"></a>#pragma sağlama toplamı (C# Başvurusu)
Hata ayıklama ASP.NET sayfalarına yardımcı olmak için kaynak dosyaları için denetimler oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```csharp
#pragma checksum "filename" "{guid}" "checksum bytes"  
```  
  
## <a name="parameters"></a>Parametreler  
 `"filename"`  
 Değişiklikler veya güncelleştirmeler için izleme gerektiren dosyanın adı.  
  
 `"{guid}"`  
 Karma algoritmaiçin Genel Olarak Benzersiz Tanımlayıcı (GUID).  
  
 `"checksum_bytes"`  
 Çeklerin baytlarını temsil eden hexadecimal basamaklar dizesi. Hexadecimal basamakların çift sayısı olmalı. Tek sayıda basamak, derleme zamanı uyarısı ile sonuçlanır ve yönerge yoksayılır.  
  
## <a name="remarks"></a>Açıklamalar  
 Visual Studio hata ayıklama her zaman doğru kaynağı bulduğundan emin olmak için bir checksum kullanır. Derleyici bir kaynak dosya için denetim umunu hesaplar ve çıktıyı program veritabanı (PDB) dosyasına yalar. Hata ayıklama, kaynak dosyayı hesapladığını denetler karşıkarşılaştırmak için PDB'yi kullanır.  
  
 Bu çözüm, ASP.NET projelerde çalışmaz, çünkü hesaplanmış denetimler .aspx dosyası yerine oluşturulan kaynak dosya içindir. Bu sorunu gidermek `#pragma checksum` için, ASP.NET sayfaları için checksum desteği sağlar.  
  
 Visual C#'da bir ASP.NET projesi oluşturduğunuzda, oluşturulan kaynak dosyası,.kaynak dosyanın oluşturulduğu .aspx dosyası için bir denetim umumu içerir. Derleyici daha sonra bu bilgileri PDB dosyasına yazar.  
  
 Derleyici dosyada yönergeyle `#pragma checksum` karşılaşmazsa, denetimleri hesaplar ve değeri PDB dosyasına yazar.  
  
## <a name="example"></a>Örnek  
  
```csharp
class TestClass  
{  
    static int Main()  
    {  
        #pragma checksum "file.cs" "{406EA660-64CF-4C82-B6F0-42D48172A799}" "ab007f1d23d9" // New checksum  
    }  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Önİşleme İşlemciler Direktifleri](./index.md)
