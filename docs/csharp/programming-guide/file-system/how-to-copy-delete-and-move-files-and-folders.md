---
title: Dosyaları ve klasörleri kopyalama, silme ve taşıma-C# Programlama Kılavuzu
description: Dosya, dizin, FileInfo ve DirectoryInfo sınıflarını kullanarak dosya ve klasörleri kopyalama, silme ve taşıma hakkında bilgi edinin.
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
ms.openlocfilehash: 208502651080f4fd614e34d1bf5b088dfb1207a6
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303367"
---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a>Dosyaları ve klasörleri kopyalama, silme ve taşıma (C# Programlama Kılavuzu)
Aşağıdaki örneklerde, <xref:System.IO.File?displayProperty=nameWithType> <xref:System.IO.Directory?displayProperty=nameWithType> ad alanından,, <xref:System.IO.FileInfo?displayProperty=nameWithType> ve <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> sınıfları kullanarak dosya ve klasörleri zaman uyumlu bir şekilde kopyalama, taşıma ve silme işlemlerinin nasıl yapılacağı gösterilmektedir <xref:System.IO?displayProperty=nameWithType> . Bu örnekler, bir ilerleme çubuğu veya başka bir kullanıcı arabirimi sağlamaz. Standart ilerleme durumu iletişim kutusu sağlamak istiyorsanız, bkz. [dosya işlemleri için ilerleme durumu iletişim kutusu sağlama](how-to-provide-a-progress-dialog-box-for-file-operations.md).  
  
 <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType>Birden çok dosya üzerinde çalışırken ilerlemeyi hesaplamanıza olanak sağlayacak olayları sağlamak için kullanın. Diğer bir yaklaşım, Windows kabuğu 'nda dosyayla ilgili ilgili yöntemleri çağırmak için platform çağırma kullanmaktır. Bu dosya işlemlerini zaman uyumsuz olarak gerçekleştirme hakkında daha fazla bilgi için bkz. [zaman uyumsuz dosya g/ç](../../../standard/io/asynchronous-file-i-o.md).  
  
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
- [Dosya Sistemi ve Kayıt Defteri (C# Programlama Kılavuzu)](index.md)
- [Dosya işlemleri için ilerleme durumu iletişim kutusu sağlama](how-to-provide-a-progress-dialog-box-for-file-operations.md)
- [Dosya ve akış g/ç](../../../standard/io/index.md)
- [Ortak g/ç görevleri](../../../standard/io/common-i-o-tasks.md)
