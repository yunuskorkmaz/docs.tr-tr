---
title: 'Nasıl yapılır: Dosya ve dizinleri yalıtılmış depolamadaki Sil'
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d05b7fa3010ab089d1a97e9a0516096326fd4bb6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54538030"
---
# <a name="how-to-delete-files-and-directories-in-isolated-storage"></a>Nasıl yapılır: Dosya ve dizinleri yalıtılmış depolamadaki Sil
Dizinleri ve bir yalıtılmış depolama dosyasında dosyaları silebilirsiniz. Bir depo içindeki dosya ve dizin adları, işletim sistemi bağımlıdır ve köküne sanal dosya sistemi olarak belirtilir. Bunlar, Windows işletim sistemlerinde büyük küçük harfe duyarlı değildir.  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType> Sınıf dizinleri ve dosyaları silmek için iki yöntem sunar: <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> ve <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>. Bir <xref:System.IO.IsolatedStorage.IsolatedStorageException> özel durumu, bir dosya veya dizin yok silmeye çalışırsanız oluşur. Adı, bir joker karakter içeriyorsa <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> oluşturur bir <xref:System.IO.IsolatedStorage.IsolatedStorageException> özel durumu ve <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> oluşturur bir <xref:System.ArgumentException> özel durum.  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> Dizin herhangi bir dosya veya alt dizinler içeriyorsa yöntem başarısız olur. Kullanabileceğiniz <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> ve <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> mevcut dosya ve dizinleri almak için yöntemler. Sanal dosya sisteminde bir deposunun arama hakkında daha fazla bilgi için bkz. [nasıl yapılır: Yalıtılmış depolamada mevcut dosya ve dizinleri bulma](../../../docs/standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği oluşturur ve ardından çeşitli dizinleri ve dosyaları siler.  
  
 [!code-cpp[Conceptual.IsolatedStorage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.IsolatedStorage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source4.cs#4)]
 [!code-vb[Conceptual.IsolatedStorage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source4.vb#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType>
- [Yalıtılmış Depolama](../../../docs/standard/io/isolated-storage.md)
