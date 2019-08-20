---
title: 'Nasıl yapılır: Dosyaları ve klasörleri kopyalama, silme ve taşıma- C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
ms.openlocfilehash: dd32798062dbfc9a10acd27ce51d8d5dd3b164f6
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590092"
---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a>Nasıl yapılır: Dosyaları ve klasörleri kopyalama, silme ve taşıma (C# Programlama Kılavuzu)
Aşağıdaki <xref:System.IO.File?displayProperty=nameWithType>örneklerde, ad<xref:System.IO?displayProperty=nameWithType> alanından <xref:System.IO.FileInfo?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, ve <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> sınıfları kullanarak dosya ve klasörleri zaman uyumlu bir şekilde kopyalama, taşıma ve silme işlemlerinin nasıl yapılacağı gösterilmektedir. Bu örnekler, bir ilerleme çubuğu veya başka bir kullanıcı arabirimi sağlamaz. Standart ilerleme durumu iletişim kutusu sağlamak istiyorsanız, bkz [. nasıl yapılır: Dosya Işlemleri](how-to-provide-a-progress-dialog-box-for-file-operations.md)Için bir Ilerleme durumu iletişim kutusu belirtin.  
  
 Birden <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> çok dosya üzerinde çalışırken ilerlemeyi hesaplamanıza olanak sağlayacak olayları sağlamak için kullanın. Diğer bir yaklaşım, Windows kabuğu 'nda dosyayla ilgili ilgili yöntemleri çağırmak için platform çağırma kullanmaktır. Bu dosya işlemlerini zaman uyumsuz olarak gerçekleştirme hakkında daha fazla bilgi için bkz. [zaman uyumsuz dosya g/ç](../../../standard/io/asynchronous-file-i-o.md).  
  
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
- [Nasıl yapılır: Dosya Işlemleri için Ilerleme durumu Iletişim kutusu sağlama](how-to-provide-a-progress-dialog-box-for-file-operations.md)
- [Dosya ve Akış G/Ç'si](../../../standard/io/index.md)
- [Ortak G/Ç Görevleri](../../../standard/io/common-i-o-tasks.md)
