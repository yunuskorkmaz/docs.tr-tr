---
title: 'Nasıl yapılır: Dosyaları ve Klasörleri Kopyalama, Silme ve Taşıma (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
ms.openlocfilehash: ea7e23f03f4321644eb2484b3965a0de3f180c47
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43504541"
---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a>Nasıl yapılır: Dosyaları ve Klasörleri Kopyalama, Silme ve Taşıma (C# Programlama Kılavuzu)
Aşağıdaki örnekler kopyalayın, taşıma ve dosya ve klasörleri kullanarak zaman uyumlu bir şekilde silmek nasıl <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType>, ve <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> gelen sınıflar <xref:System.IO?displayProperty=nameWithType> ad alanı. Bu örneklerde bir ilerleme çubuğu veya herhangi bir kullanıcı arabirimi sağlamaz. Standart ilerleme durumu iletişim kutusu sağlamak istiyorsanız, bkz. [nasıl yapılır: dosya işlemleri için ilerleme durumu iletişim kutusu sağlama](how-to-provide-a-progress-dialog-box-for-file-operations.md).  
  
 Kullanım <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> , birden çok dosya çalışırken ilerleme durumunu hesapla olanak tanıyacak olayları sağlamak için. Başka bir yaklaşım platform kullanmaktır. Windows Kabuğu'nda ilgili dosya ile ilgili yöntemleri çağırmak için çağır. Bu dosya işlemlerini zaman uyumsuz olarak gerçekleştirme hakkında daha fazla bilgi için bkz: [zaman uyumsuz dosya g/ç](https://msdn.microsoft.com/library/kztecsys).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, dosya ve dizinleri kopyalama gösterilmektedir.  
  
 [!code-csharp[csFilesandFolders#7](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_1.cs)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, dosya ve dizinleri taşıma gösterilmektedir.  
  
 [!code-csharp[csFilesandFolders#8](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_2.cs)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, dosyaları ve dizinleri silme işlemini gösterir.  
  
 [!code-csharp[csFilesandFolders#9](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_3.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- <xref:System.IO?displayProperty=nameWithType>  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Dosya sistemi ve kayıt defteri (C# programlama Kılavuzu)](index.md)  
- [Nasıl yapılır: Dosya İşlemleri için İlerleme Durumu İletişim Kutusu Sağlama](how-to-provide-a-progress-dialog-box-for-file-operations.md)  
- [Dosya ve Akış G/Ç'si](https://msdn.microsoft.com/library/k3352a4t)  
- [Ortak G/Ç Görevleri](https://msdn.microsoft.com/library/ms404278)
