---
title: Dosya ve klasörleri kopyalama, silme ve taşıma - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
ms.openlocfilehash: 662f0ab3b9e69aa8bfb0085f42f577b850029e4d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712279"
---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a>Dosya ve klasörleri kopyalama, silme ve taşıma (C# Programlama Kılavuzu)
Aşağıdaki örnekler, <xref:System.IO.File?displayProperty=nameWithType> <xref:System.IO.Directory?displayProperty=nameWithType> <xref:System.IO.FileInfo?displayProperty=nameWithType> <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> <xref:System.IO?displayProperty=nameWithType> ad alanından , , ve sınıfları kullanarak dosya ve klasörleri eşzamanlı bir şekilde kopyalama, taşıma ve silme yi gösterir. Bu örnekler bir ilerleme çubuğu veya başka bir kullanıcı arabirimi sağlamaz. Standart bir ilerleme iletişim kutusu sağlamak istiyorsanız, [dosya işlemleri için ilerleme iletişim kutusunun nasıl sağlayabileceğinize](how-to-provide-a-progress-dialog-box-for-file-operations.md)bakın.  
  
 Birden <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> çok dosya üzerinde çalışırken ilerlemeyi hesaplamanızı sağlayacak olayları sağlamak için kullanın. Diğer bir yaklaşım, Windows Shell'deki ilgili dosya yla ilgili yöntemleri çağırmak için platform çağrısı kullanmaktır. Bu dosya işlemlerinin eş senkronize olarak nasıl gerçekleştirilecek hakkında bilgi [için, Bkz.](../../../standard/io/asynchronous-file-i-o.md)  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, dosyaların ve dizinlerin nasıl kopyalanılsüreceğini gösterir.  
  
 [!code-csharp[csFilesandFolders#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#7)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, dosyaların ve dizinlerin nasıl taşınır olduğunu gösterir.  
  
 [!code-csharp[csFilesandFolders#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#8)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, dosyaların ve dizinlerin nasıl silineceklerini gösterir.  
  
 [!code-csharp[csFilesandFolders#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#9)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO?displayProperty=nameWithType>
- [C# Programlama Kılavuzu](../index.md)
- [Dosya Sistemi ve Kayıt Defteri (C# Programlama Kılavuzu)](index.md)
- [Dosya işlemleri için ilerleme durumu iletişim kutusu sağlama](how-to-provide-a-progress-dialog-box-for-file-operations.md)
- [Dosya ve Akış G/Ç'si](../../../standard/io/index.md)
- [Ortak G/Ç Görevleri](../../../standard/io/common-i-o-tasks.md)
