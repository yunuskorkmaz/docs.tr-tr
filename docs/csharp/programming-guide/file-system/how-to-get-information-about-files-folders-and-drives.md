---
title: Dosyalar, klasörler ve sürücüler hakkında bilgi edinme - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- files [C#], getting information about
ms.assetid: 22fc2da6-5494-405b-995e-c0b99142a93e
ms.openlocfilehash: 6024b1be4ce826900c6f9b367323fb19ac55d2c7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705216"
---
# <a name="how-to-get-information-about-files-folders-and-drives--c-programming-guide"></a>Dosyalar, klasörler ve sürücüler hakkında bilgi edinme (C# Programlama Kılavuzu)
.NET Framework'de aşağıdaki sınıfları kullanarak dosya sistemi bilgilerine erişebilirsiniz:  
  
- <xref:System.IO.FileInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.DirectoryInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.DriveInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.Directory?displayProperty=nameWithType>  
  
- <xref:System.IO.File?displayProperty=nameWithType>  
  
 Ve <xref:System.IO.FileInfo> <xref:System.IO.DirectoryInfo> sınıflar bir dosya veya dizin temsil eder ve NTFS dosya sistemi tarafından desteklenen dosya özniteliklerinin çoğunu ortaya çıkaran özellikler içerir. Ayrıca dosya ve klasörleri açma, kapatma, taşıma ve silme yöntemleri de içerir. Dosyanın, klasörün veya sürücünün adını temsil eden bir dizeyi oluşturarak bu sınıfların örneklerini oluşturabilirsiniz:  
  
```csharp  
System.IO.DriveInfo di = new System.IO.DriveInfo(@"C:\");  
```  
  
 Ayrıca, " <xref:System.IO.DirectoryInfo.GetDirectories%2A?displayProperty=nameWithType> <xref:System.IO.DirectoryInfo.GetFiles%2A?displayProperty=nameWithType>ve <xref:System.IO.DriveInfo.RootDirectory%2A?displayProperty=nameWithType>.  
  
 Ve <xref:System.IO.Directory?displayProperty=nameWithType> <xref:System.IO.File?displayProperty=nameWithType> sınıflar dizinler ve dosyalar hakkında bilgi almak için statik yöntemler sağlar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, dosya ve klasörler hakkındaki bilgilere erişmek için çeşitli yolları gösterir.  
  
 [!code-csharp[csFilesandFolders#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#6)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Kullanıcı tarafından belirtilen yol dizelerini işlerken, aşağıdaki koşullar için özel durumları da işlemeniz gerekir:  
  
- Dosya adı yanlış biçimlendirilmiş. Örneğin, geçersiz karakterler veya yalnızca beyaz boşluk içerir.  
  
- Dosya adı null.  
  
- Dosya adı, sistem tarafından tanımlanan maksimum uzunluktan daha uzundur.  
  
- Dosya adı bir üst üste (:) içerir.  
  
 Uygulama belirtilen dosyayı okumak için yeterli izine `Exists` sahip `false` değilse, yöntem bir yol var olup olmadığına bakılmaksızın döndürür; yöntem bir özel durum atmaz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO?displayProperty=nameWithType>
- [C# Programlama Kılavuzu](../index.md)
- [Dosya Sistemi ve Kayıt Defteri (C# Programlama Kılavuzu)](./index.md)
