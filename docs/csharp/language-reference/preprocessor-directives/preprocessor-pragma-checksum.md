---
title: '#pragma sağlama - C# başvurusu'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#pragma checksum'
helpviewer_keywords:
- '#pragma checksum [C#]'
ms.assetid: 3673e4ca-6098-4ec1-890f-8fceb2a794a2
ms.openlocfilehash: 36e5602f0a0b872a4aa6cdac64b49b1d1c708795
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65877521"
---
# <a name="pragma-checksum-c-reference"></a>#pragma sağlama toplamı (C# Başvurusu)
ASP.NET sayfaları hatalarını ayıklamaya yardımcı olmak kaynak dosyalar için sağlama toplamları oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```csharp
#pragma checksum "filename" "{guid}" "checksum bytes"  
```  
  
## <a name="parameters"></a>Parametreler  
 `"filename"`  
 İzleme gerektiren değişiklikleri veya güncelleştirmeleri için dosyanın adı.  
  
 `"{guid}"`  
 Genel benzersiz tanıtıcısı (GUID) karma algoritması için.  
  
 `"checksum_bytes"`  
 Sağlama toplamı baytını temsil eden bir onaltılık basamak dizisi. Onaltı basamaklı bir çift sayı olmalıdır. Bir derleme zamanı uyarı ve yönerge basamak sonuçları tek sayıda göz ardı edilir.  
  
## <a name="remarks"></a>Açıklamalar  
 Visual Studio hata ayıklayıcı her zaman doğru kaynak bulduğu emin olmak için bir sağlama toplamı kullanır. Derleyici, bir kaynak dosyası için sağlama toplamını hesaplar ve ardından program veritabanı (PDB) dosyası çıktıyı yayar. Hata ayıklayıcı, PDB sonra kaynak dosyasını hesaplar sağlama toplamı karşılaştırma için kullanır.  
  
 Bu çözüm, .aspx dosyası yerine üretilen kaynak dosyası için hesaplanan sağlama toplamı olduğu için ASP.NET projeleri için çalışmaz. Bu sorunu gidermek için `#pragma checksum` ASP.NET sayfaları için sağlama toplamı desteği sağlar.  
  
 Görselde bir ASP.NET projesi oluşturduğunuzda, C#, üretilen kaynak dosyası içinden kaynak oluşturulduğunda .aspx dosyası, bir sağlama toplamı içeriyor. Derleyici, daha sonra bu bilgileri PDB dosyasına yazar.  
  
 Derleyici Hayır karşılaşırsa `#pragma checksum` dosyasındaki yönergesi, sağlama toplamını hesaplar ve değeri PDB dosyasına yazar.  
  
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

- [C# başvurusu](../../../csharp/language-reference/index.md)
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [C# Ön İşlemci Yönergeleri](../../../csharp/language-reference/preprocessor-directives/index.md)
