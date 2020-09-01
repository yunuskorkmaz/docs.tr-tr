---
description: '#pragma sağlama toplamı-C# başvurusu'
title: '#pragma sağlama toplamı-C# başvurusu'
ms.date: 07/20/2015
f1_keywords:
- '#pragma checksum'
helpviewer_keywords:
- '#pragma checksum [C#]'
ms.assetid: 3673e4ca-6098-4ec1-890f-8fceb2a794a2
ms.openlocfilehash: 60c491000337fd50da217e97054e86faccb2e7d7
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89137987"
---
# <a name="pragma-checksum-c-reference"></a>#pragma sağlama toplamı (C# Başvurusu)
ASP.NET sayfalarında hata ayıklamaya yardımcı olmak için kaynak dosyaları için sağlama toplamı üretir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```csharp
#pragma checksum "filename" "{guid}" "checksum bytes"  
```  
  
## <a name="parameters"></a>Parametreler  
 `"filename"`  
 Değişiklik veya güncelleştirme için izlemeyi gerektiren dosyanın adı.  
  
 `"{guid}"`  
 Karma algoritma için genel benzersiz tanımlayıcı (GUID).  
  
 `"checksum_bytes"`  
 Sağlama toplamı baytlarını temsil eden onaltılık basamakların dizesi. Çift sayıda onaltılık basamak olmalıdır. Tek sayıda basamak derleme zamanı uyarısına neden olur ve yönerge yok sayılır.  
  
## <a name="remarks"></a>Açıklamalar  
 Visual Studio hata ayıklayıcı, her zaman doğru kaynağı bulmasını sağlamak için bir sağlama toplamı kullanır. Derleyici, kaynak dosya için sağlama toplamını hesaplar ve sonra çıktıyı program veritabanı (PDB) dosyasına yayar. Hata ayıklayıcı daha sonra kaynak dosya için hesapladığı sağlama toplamıyla karşılaştırmak için PDB 'yi kullanır.  
  
 Hesaplanan sağlama toplamı,. aspx dosyası yerine oluşturulan kaynak dosya için olduğundan, bu çözüm ASP.NET projelerinde çalışmaz. Bu sorunu gidermek için `#pragma checksum` ASP.NET sayfaları için sağlama toplamı desteği sağlar.  
  
 Visual C# içinde bir ASP.NET projesi oluşturduğunuzda oluşturulan kaynak dosya, kaynağın oluşturulduğu. aspx dosyası için bir sağlama toplamı içerir. Derleyici daha sonra bu bilgileri PDB dosyasına yazar.  
  
 Derleyici `#pragma checksum` dosyada hiçbir yönergeyle karşılaşırsa, sağlama toplamını hesaplar ve DEĞERI pdb dosyasına yazar.  
  
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

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Önişlemci yönergeleri](./index.md)
