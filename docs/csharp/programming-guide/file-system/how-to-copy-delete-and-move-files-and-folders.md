---
title: Dosyaları ve klasörleri kopyalama, silme ve taşıma- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
ms.openlocfilehash: 662f0ab3b9e69aa8bfb0085f42f577b850029e4d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712279"
---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a>Dosyaları ve klasörleri kopyalama, silme ve taşıma (C# Programlama Kılavuzu)
Aşağıdaki örneklerde, <xref:System.IO?displayProperty=nameWithType> ad alanındaki <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType>ve <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> sınıflarını kullanarak dosya ve klasörleri zaman uyumlu bir şekilde kopyalama, taşıma ve silme işlemlerinin nasıl yapılacağı gösterilmektedir. Bu örnekler, bir ilerleme çubuğu veya başka bir kullanıcı arabirimi sağlamaz. Standart ilerleme durumu iletişim kutusu sağlamak istiyorsanız, bkz. [dosya işlemleri için ilerleme durumu iletişim kutusu sağlama](how-to-provide-a-progress-dialog-box-for-file-operations.md).  
  
 Birden çok dosya üzerinde çalışırken ilerlemeyi hesaplamanıza olanak sağlayacak olayları sağlamak için <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> kullanın. Diğer bir yaklaşım, Windows kabuğu 'nda dosyayla ilgili ilgili yöntemleri çağırmak için platform çağırma kullanmaktır. Bu dosya işlemlerini zaman uyumsuz olarak gerçekleştirme hakkında daha fazla bilgi için bkz. [zaman uyumsuz dosya g/ç](../../../standard/io/asynchronous-file-i-o.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, dosyaların ve dizinlerin nasıl kopyalanacağını gösterir.  
  
 [!code-csharp[csFilesandFolders#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#7)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, dosyaların ve dizinlerin nasıl taşınacağını gösterir.  
  
 [!code-csharp[csFilesandFolders#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#8)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, dosyaların ve dizinlerin nasıl silineceğini gösterir.  
  
 [!code-csharp[csFilesandFolders#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#9)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO?displayProperty=nameWithType>
- [C# Programlama Kılavuzu](../index.md)
- [Dosya sistemi ve kayıt defteri (C# Programlama Kılavuzu)](index.md)
- [Dosya işlemleri için ilerleme durumu iletişim kutusu sağlama](how-to-provide-a-progress-dialog-box-for-file-operations.md)
- [Dosya ve Akış G/Ç'si](../../../standard/io/index.md)
- [Ortak G/Ç Görevleri](../../../standard/io/common-i-o-tasks.md)
