---
title: 'Nasıl yapılır: Yalıtılmış Depolamadaki Dosya ve Dizinleri Silme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data storage using isolated storage, deleting files and directories
- directories [.NET Framework], isolated storage
- files [.NET Framework], isolated storage
- isolated storage, deleting files and directories
- data stores, deleting files and directories
- stores, creating files and directories
- deleting files within isolated stage file
- storing data using isolated storage, deleting files and directories
- deleting directories within isolated stage file
ms.assetid: 8fcc0dea-435b-4d40-ba4d-ba056265c202
ms.openlocfilehash: ec4de3e3a139cfcf66f1f6252c03c467f4ccfbc5
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75707863"
---
# <a name="how-to-delete-files-and-directories-in-isolated-storage"></a>Nasıl yapılır: Yalıtılmış Depolamadaki Dosya ve Dizinleri Silme
Yalıtılmış bir depolama dosyası içindeki dizinleri ve dosyaları silebilirsiniz. Bir mağaza içinde, dosya ve Dizin adları işletim sistemine bağımlıdır ve sanal dosya sisteminin köküne göreli olarak belirtilir. Windows işletim sistemlerinde büyük/küçük harfe duyarlı değildir.  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType> sınıfı dizinleri ve dosyaları silmek için iki yöntem sunar: <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> ve <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>. Varolmayan bir dosyayı veya dizini silmeye çalıştığınızda bir <xref:System.IO.IsolatedStorage.IsolatedStorageException> özel durumu oluşturulur. Ada bir joker karakter eklerseniz, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> bir <xref:System.IO.IsolatedStorage.IsolatedStorageException> özel durumu atar ve <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> bir <xref:System.ArgumentException> özel durumu oluşturur.  
  
 Dizin herhangi bir dosya veya alt dizin içeriyorsa <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> yöntemi başarısız olur. Mevcut dosya ve dizinleri almak için <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> ve <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> yöntemlerini kullanabilirsiniz. Bir deponun sanal dosya sistemini arama hakkında daha fazla bilgi için bkz. [nasıl yapılır: yalıtılmış depolamada mevcut dosya ve dizinleri bulma](../../../docs/standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, birkaç dizin ve dosyayı oluşturur ve siler.  
  
 [!code-cpp[Conceptual.IsolatedStorage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.IsolatedStorage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source4.cs#4)]
 [!code-vb[Conceptual.IsolatedStorage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source4.vb#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType>
- [Yalıtılmış Depolama](../../../docs/standard/io/isolated-storage.md)
