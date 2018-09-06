---
title: '#pragma sağlama toplamı (C# Başvurusu)'
ms.date: 07/20/2015
f1_keywords:
- '#pragma checksum'
helpviewer_keywords:
- '#pragma checksum [C#]'
ms.assetid: 3673e4ca-6098-4ec1-890f-8fceb2a794a2
ms.openlocfilehash: 28a9ccfb9d36e648304a177294904ab1b7f18892
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43741324"
---
# <a name="pragma-checksum-c-reference"></a>#pragma sağlama toplamı (C# Başvurusu)
Hata ayıklamaya yardımcı olmak kaynak dosyalar için sağlama toplamları oluşturur [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] sayfaları.  
  
## <a name="syntax"></a>Sözdizimi  
  
```csharp
#pragma checksum "filename" "{guid}" "checksum bytes"  
```  
  
#### <a name="parameters"></a>Parametreler  
 `"filename"`  
 İzleme gerektiren değişiklikleri veya güncelleştirmeleri için dosyanın adı.  
  
 `"{guid}"`  
 Genel benzersiz tanıtıcısı (GUID) karma algoritması için.  
  
 `"checksum_bytes"`  
 Sağlama toplamı baytını temsil eden bir onaltılık basamak dizisi. Onaltı basamaklı bir çift sayı olmalıdır. Bir derleme zamanı uyarı ve yönerge basamak sonuçları tek sayıda göz ardı edilir.  
  
## <a name="remarks"></a>Açıklamalar  
 Visual Studio hata ayıklayıcı her zaman doğru kaynak bulduğu emin olmak için bir sağlama toplamı kullanır. Derleyici, bir kaynak dosyası için sağlama toplamını hesaplar ve ardından program veritabanı (PDB) dosyası çıktıyı yayar. Hata ayıklayıcı, PDB sonra kaynak dosyasını hesaplar sağlama toplamı karşılaştırma için kullanır.  
  
 Bu çözüm için çalışmaz [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] .aspx dosyası yerine üretilen kaynak dosyası için hesaplanan sağlama toplamı olduğu için proje. Bu sorunu gidermek için `#pragma checksum` sağlama desteği sağlayan [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] sayfaları.  
  
 Oluştururken bir [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] projesini Visual C# içinde oluşturulan kaynak dosyayı içeren içinden kaynak oluşturulduğunda .aspx dosyası, bir sağlama toplamı. Derleyici, daha sonra bu bilgileri PDB dosyasına yazar.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# Ön İşlemci Yönergeleri](../../../csharp/language-reference/preprocessor-directives/index.md)
