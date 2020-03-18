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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75707863"
---
# <a name="how-to-delete-files-and-directories-in-isolated-storage"></a>Nasıl yapılır: Yalıtılmış Depolamadaki Dosya ve Dizinleri Silme
İznileri ve dosyaları yalıtılmış bir depolama dosyası içinde silebilirsiniz. Bir mağaza içinde, dosya ve dizin adları işletim sistemine bağlıdır ve sanal dosya sisteminin köküne göre belirtilir. Windows işletim sistemlerinde büyük/küçük harf duyarlı değildir.  
  
 Sınıf, <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType> dizinleri ve dosyaları silen <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>iki yöntem sağlar: ve. Var <xref:System.IO.IsolatedStorage.IsolatedStorageException> olmayan bir dosyayı veya dizini silmeye çalışırsanız bir özel durum atılır. Adına bir joker karakter eklerseniz, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> bir <xref:System.IO.IsolatedStorage.IsolatedStorageException> özel durum <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> atar <xref:System.ArgumentException> ve bir özel durum atar.  
  
 Dizin <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> herhangi bir dosya veya alt dizin içeriyorsa yöntem başarısız olur. Varolan dosyaları <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> ve dizinleri almak için ve yöntemleri kullanabilirsiniz. Bir mağazanın sanal dosya sisteminde arama hakkında daha fazla bilgi için [bkz.](../../../docs/standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md)  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği birkaç dizin ve dosya oluşturur ve sonra siler.  
  
 [!code-cpp[Conceptual.IsolatedStorage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.IsolatedStorage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source4.cs#4)]
 [!code-vb[Conceptual.IsolatedStorage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source4.vb#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType>
- [Yalıtılmış Depolama](../../../docs/standard/io/isolated-storage.md)
