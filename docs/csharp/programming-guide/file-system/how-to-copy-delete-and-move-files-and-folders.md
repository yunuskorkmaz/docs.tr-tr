---
title: "Nasıl yapılır: Dosyaları ve Klasörleri Kopyalama, Silme ve Taşıma (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 56383873674998fc0d6417a2abf4fa72e498f08f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a>Nasıl yapılır: Dosyaları ve Klasörleri Kopyalama, Silme ve Taşıma (C# Programlama Kılavuzu)
Aşağıdaki örnekler nasıl kopyalama, taşıma ve dosya ve klasörlerin zaman uyumlu bir biçimde kullanarak silme <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType>, ve <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> gelen sınıfları <xref:System.IO?displayProperty=nameWithType> ad alanı. Bu örnekler, bir ilerleme çubuğu veya herhangi bir kullanıcı arabirimi sağlamaz. Standart ilerleme durumu iletişim kutusu sağlamak istiyorsanız, bkz: [nasıl yapılır: dosya işlemleri için ilerleme durumu iletişim kutusu sağlama](how-to-provide-a-progress-dialog-box-for-file-operations.md).  
  
 Kullanım <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> , birden çok dosya çalışırken ilerleme durumunu hesaplamak sağlayacaktır olaylarını sağlamak için. Başka bir yaklaşım platform kullanmaktır Windows Kabuğu'nda ilgili dosya ile ilgili yöntemleri çağırmak için çağırma. Bu dosya işlemlerini zaman uyumsuz olarak gerçekleştirme hakkında daha fazla bilgi için bkz: [zaman uyumsuz dosya g/ç](https://msdn.microsoft.com/library/kztecsys).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, dosyaları ve dizinleri kopyalamak gösterilmiştir.  
  
 [!code-csharp[csFilesandFolders#7](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_1.cs)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, dosyaları ve dizinleri taşımak gösterilmiştir.  
  
 [!code-csharp[csFilesandFolders#8](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_2.cs)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, dosya ve dizinleri silme gösterilmektedir.  
  
 [!code-csharp[csFilesandFolders#9](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_3.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IO?displayProperty=nameWithType>  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Dosya sistemi ve kayıt defteri (C# programlama Kılavuzu)](index.md)  
 [Nasıl yapılır: dosya işlemleri için ilerleme durumu iletişim kutusu sağlama](how-to-provide-a-progress-dialog-box-for-file-operations.md)  
 [Dosya ve akış g/ç](https://msdn.microsoft.com/library/k3352a4t)  
 [Ortak g/ç görevleri](https://msdn.microsoft.com/library/ms404278)
