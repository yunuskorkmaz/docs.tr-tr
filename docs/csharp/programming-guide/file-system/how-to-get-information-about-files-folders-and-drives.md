---
title: Dosyalar, klasörler ve sürücüler hakkında bilgi edinme- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- files [C#], getting information about
ms.assetid: 22fc2da6-5494-405b-995e-c0b99142a93e
ms.openlocfilehash: 6024b1be4ce826900c6f9b367323fb19ac55d2c7
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705216"
---
# <a name="how-to-get-information-about-files-folders-and-drives--c-programming-guide"></a>Dosyalar, klasörler ve sürücüler hakkında bilgi alma (C# Programlama Kılavuzu)
.NET Framework, aşağıdaki sınıfları kullanarak dosya sistemi bilgilerine erişebilirsiniz:  
  
- <xref:System.IO.FileInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.DirectoryInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.DriveInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.Directory?displayProperty=nameWithType>  
  
- <xref:System.IO.File?displayProperty=nameWithType>  
  
 <xref:System.IO.FileInfo> ve <xref:System.IO.DirectoryInfo> sınıfları bir dosyayı veya dizini temsil eder ve NTFS dosya sistemi tarafından desteklenen dosya özniteliklerinin çoğunu ortaya çıkaran özellikler içerir. Ayrıca dosya ve klasörleri açma, kapatma, taşıma ve silme yöntemleri de bulunur. Oluşturucuya dosya, klasör veya sürücü adını temsil eden bir dize geçirerek, bu sınıfların örneklerini oluşturabilirsiniz:  
  
```csharp  
System.IO.DriveInfo di = new System.IO.DriveInfo(@"C:\");  
```  
  
 Ayrıca, <xref:System.IO.DirectoryInfo.GetDirectories%2A?displayProperty=nameWithType>, <xref:System.IO.DirectoryInfo.GetFiles%2A?displayProperty=nameWithType>ve <xref:System.IO.DriveInfo.RootDirectory%2A?displayProperty=nameWithType>için çağrılar kullanarak dosyaların, klasörlerin veya sürücülerin adlarını elde edebilirsiniz.  
  
 <xref:System.IO.Directory?displayProperty=nameWithType> ve <xref:System.IO.File?displayProperty=nameWithType> sınıfları, dizinler ve dosyalar hakkında bilgi almak için statik yöntemler sağlar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek dosya ve klasörlerle ilgili bilgilere erişmek için çeşitli yollar gösterir.  
  
 [!code-csharp[csFilesandFolders#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#6)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Kullanıcı tarafından belirtilen yol dizelerini işlerken aşağıdaki koşullarda özel durumları da işlemeniz gerekir:  
  
- Dosya adı hatalı biçimlendirilmiş. Örneğin, geçersiz karakterler veya yalnızca boşluk içeriyor.  
  
- Dosya adı null.  
  
- Dosya adı sistem tarafından tanımlanan uzunluk üst sınırından daha uzun.  
  
- Dosya adı iki nokta üst üste (:)) sahiptir.  
  
 Uygulamanın belirtilen dosyayı okumak için yeterli izni yoksa, `Exists` yöntemi bir yolun var olup olmadığına bakılmaksızın `false` döndürür; Yöntem bir özel durum oluşturmaz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO?displayProperty=nameWithType>
- [C# Programlama Kılavuzu](../index.md)
- [Dosya sistemi ve kayıt defteri (C# Programlama Kılavuzu)](./index.md)
