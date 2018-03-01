---
title: "#pragma sağlama toplamı (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#pragma checksum'
helpviewer_keywords:
- '#pragma checksum [C#]'
ms.assetid: 3673e4ca-6098-4ec1-890f-8fceb2a794a2
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0604a559be25c300fcdc6041975306b465fc595f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="pragma-checksum-c-reference"></a>#pragma sağlama toplamı (C# Başvurusu)
Hata ayıklamaya yardımcı olmak kaynak dosyaları için sağlama oluşturur [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] sayfaları.  
  
## <a name="syntax"></a>Sözdizimi  
  
```csharp
#pragma checksum "filename" "{guid}" "checksum bytes"  
```  
  
#### <a name="parameters"></a>Parametreler  
 `"filename"`  
 İzleme gerektiren değişiklikler veya güncelleştirmeler için dosyanın adı.  
  
 `"{guid}"`  
 Genel benzersiz tanımlayıcı (GUID) dosyası için.  
  
 `"checksum_bytes"`  
 Onaltılık basamak sağlama toplamı baytını temsil eden dize. Onaltılık basamak sayısı bir çift sayı olmalıdır. Derleme zamanı uyarı ve yönergesi basamak sonuçlarında tek sayıda göz ardı edilir.  
  
## <a name="remarks"></a>Açıklamalar  
 Visual Studio hata ayıklayıcısı bir sağlama toplamı her zaman doğru kaynak bulduğu emin olmak için kullanır. Derleyici bir kaynak dosya için sağlama toplamı hesaplar ve ardından program veritabanı (PDB) dosyası çıktıyı yayar. Hata ayıklayıcı PDB için kaynak dosyası hesaplar sağlama toplamı Karşılaştırılacak sonra kullanır.  
  
 Bu çözüm için çalışmaz [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] projeleri hesaplanan sağlama toplamı .aspx dosyası yerine oluşturulan kaynak dosya için olduğundan. Bu sorunu gidermek için `#pragma checksum` sağlama toplamı desteği sağlar [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] sayfaları.  
  
 Oluştururken bir [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] proje [!INCLUDE[csprcs](~/includes/csprcs-md.md)], sağlama toplamı, kaynak oluşturulduğunda .aspx dosyası için oluşturulan kaynak dosyası içerir. Derleyici, sonra bu bilgileri PDB dosyasına yazar.  
  
 Derleyici Hayır karşılaşırsa `#pragma checksum` yönerge dosyasında sağlama toplamı hesaplar ve değeri PDB dosyasına yazar.  
  
## <a name="example"></a>Örnek  
  
```csharp
class TestClass  
{  
    static int Main()  
    {  
        #pragma checksum "file.cs" "{3673e4ca-6098-4ec1-890f-8fceb2a794a2}" "{012345678AB}" // New checksum  
    }  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# önişlemci yönergeleri](../../../csharp/language-reference/preprocessor-directives/index.md)
