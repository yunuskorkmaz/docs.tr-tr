---
title: 'Nasıl yapılır: Kopyalama, silme, taşıma dosya ve klasörleri - C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
ms.openlocfilehash: 3e6c08050186642ceec4e2301524919379e12aaa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54527711"
---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a>Nasıl yapılır: Kopyalama, silme ve taşıma dosya ve klasörleri (C# Programlama Kılavuzu)
Aşağıdaki örnekler kopyalayın, taşıma ve dosya ve klasörleri kullanarak zaman uyumlu bir şekilde silmek nasıl <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType>, ve <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> gelen sınıflar <xref:System.IO?displayProperty=nameWithType> ad alanı. Bu örneklerde bir ilerleme çubuğu veya herhangi bir kullanıcı arabirimi sağlamaz. Standart ilerleme durumu iletişim kutusu sağlamak istiyorsanız, bkz. [nasıl yapılır: Dosya işlemleri için ilerleme durumu iletişim kutusu sağlama](how-to-provide-a-progress-dialog-box-for-file-operations.md).  
  
 Kullanım <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> , birden çok dosya çalışırken ilerleme durumunu hesapla olanak tanıyacak olayları sağlamak için. Başka bir yaklaşım platform kullanmaktır. Windows Kabuğu'nda ilgili dosya ile ilgili yöntemleri çağırmak için çağır. Bu dosya işlemlerini zaman uyumsuz olarak gerçekleştirme hakkında daha fazla bilgi için bkz: [zaman uyumsuz dosya g/ç](../../../standard/io/asynchronous-file-i-o.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, dosya ve dizinleri kopyalama gösterilmektedir.  
  
 [!code-csharp[csFilesandFolders#7](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_1.cs)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, dosya ve dizinleri taşıma gösterilmektedir.  
  
 [!code-csharp[csFilesandFolders#8](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_2.cs)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, dosyaları ve dizinleri silme işlemini gösterir.  
  
 [!code-csharp[csFilesandFolders#9](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_3.cs)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO?displayProperty=nameWithType>
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Dosya sistemi ve kayıt defteri (C# programlama Kılavuzu)](index.md)
- [Nasıl yapılır: Dosya işlemleri için ilerleme durumu iletişim kutusu sağlama](how-to-provide-a-progress-dialog-box-for-file-operations.md)
- [Dosya ve Akış G/Ç'si](../../../standard/io/index.md)
- [Ortak G/Ç Görevleri](../../../standard/io/common-i-o-tasks.md)
