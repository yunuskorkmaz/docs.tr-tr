---
title: 'Nasıl yapılır: Dosyalar, klasörler ve sürücüler - hakkında bilgi almak C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- files [C#], getting information about
ms.assetid: 22fc2da6-5494-405b-995e-c0b99142a93e
ms.openlocfilehash: e2315f5bfdca05da79e5ee4d897cd06dba6f1ed1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61681227"
---
# <a name="how-to-get-information-about-files-folders-and-drives--c-programming-guide"></a>Nasıl yapılır: Dosyalar, klasörler ve sürücüler hakkında bilgi edinin (C# Programlama Kılavuzu)
.NET Framework, dosya sistemi bilgileri aşağıdaki sınıfları kullanarak erişebilirsiniz:  
  
- <xref:System.IO.FileInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.DirectoryInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.DriveInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.Directory?displayProperty=nameWithType>  
  
- <xref:System.IO.File?displayProperty=nameWithType>  
  
 <xref:System.IO.FileInfo> Ve <xref:System.IO.DirectoryInfo> sınıfları bir dosya veya dizin temsil eder ve NTFS dosya sistemi tarafından desteklenen dosya özniteliklerin çoğu kullanıma sunan özellikler içerir. Bunlar ayrıca açma, kapatma, taşıma ve dosya ve klasörleri silme yöntemlerini içerir. Bu sınıfların örnekleri oluşturucuya dosya, klasör veya sürücüde adını temsil eden bir dize geçirerek oluşturabilirsiniz:  
  
```csharp  
System.IO.DriveInfo di = new System.IO.DriveInfo(@"C:\");  
```  
  
 Çağrıları kullanarak dosyalara, klasörlere veya sürücüleri adlarını de edinebilirsiniz <xref:System.IO.DirectoryInfo.GetDirectories%2A?displayProperty=nameWithType>, <xref:System.IO.DirectoryInfo.GetFiles%2A?displayProperty=nameWithType>, ve <xref:System.IO.DriveInfo.RootDirectory%2A?displayProperty=nameWithType>.  
  
 <xref:System.IO.Directory?displayProperty=nameWithType> Ve <xref:System.IO.File?displayProperty=nameWithType> sınıfları, dizinler ve dosyalar hakkında bilgi almak için statik yöntemler sağlar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, dosyalar ve klasörler hakkındaki bilgilere erişmek için çeşitli yollar gösterir.  
  
 [!code-csharp[csFilesandFolders#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#6)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Kullanıcı tanımlı yol dizelerini işlediğinizde, özel durumlar için aşağıdaki koşullar da işlemesi gerekir:  
  
- Dosya adı yanlış biçimlendirilmiş. Örneğin, geçersiz karakterler veya yalnızca boşluk içeriyor.  
  
- Dosya adı null.  
  
- Dosya adı sistem tarafından tanımlanan uzunluk üst sınırından daha uzun.  
  
- Dosya adı iki nokta üst üste (:) içeriyor.  
  
 Uygulama belirtilen dosyayı okumak için yeterli izinlere sahip değilse `Exists` yöntemi döndürür `false` bağımsız olarak, bir yolu var olup; yöntemi bir özel durum oluşturmaz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO?displayProperty=nameWithType>
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Dosya sistemi ve kayıt defteri (C# programlama Kılavuzu)](../../../csharp/programming-guide/file-system/index.md)
