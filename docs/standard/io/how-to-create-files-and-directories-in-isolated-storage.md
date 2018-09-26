---
title: 'Nasıl yapılır: Yalıtılmış Depolamada Dosya ve Dizinler Oluşturma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- directories [.NET Framework], isolated storage
- files [.NET Framework], isolated storage
- isolated storage, creating files and directories
- data stores, creating files and directories
- data storage using isolated storage, creating files and directories
- stores, creating files and directories
- storing data using isolated storage, creating files and directories
ms.assetid: 2ca4d2a4-809b-4f00-bc08-bf4a64d3a5c3
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 08beb44fdb58ab1c1d53f70ac0653348b96fcb18
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47157840"
---
# <a name="how-to-create-files-and-directories-in-isolated-storage"></a>Nasıl yapılır: Yalıtılmış Depolamada Dosya ve Dizinler Oluşturma
Bir yalıtılmış depolama aldıktan sonra dizin ve dosya verilerini depolamak için oluşturabilirsiniz. Bir depo dosya ve dizin adları sanal dosya sisteminin kökünü göre belirtilir.  
  
 Bir dizin oluşturmak için kullanın <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType> örnek yöntemi. Mevcut bir dizininin bir alt belirtirseniz, her iki dizini de oluşturulur. Zaten bir dizin belirtirseniz, bir dizin oluşturmadan yöntemi döndürür ve hiçbir özel durum. Ancak, bir dizin adı belirtirseniz, geçersiz karakterler içeren bir <xref:System.IO.IsolatedStorage.IsolatedStorageException> özel durumu oluşturulur.  
  
 Bir dosya oluşturmak için kullanın <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType> yöntemi.  
  
 Windows işletim sistemi, yalıtılmış depolama dosya ve dizin adlarını büyük küçük harf duyarlıdır. Diğer bir deyişle, adlı bir dosya oluşturursanız `ThisFile.txt`, ardından adlı başka bir dosya oluşturun `THISFILE.TXT`, tek bir dosya oluşturulur. Dosya adı, kendi özgün büyük/küçük harfleri görüntüleme amacıyla tutar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği bir yalıtılmış depoda dosyalar ve dizinler oluşturma işlemini göstermektedir.  
  
 [!code-csharp[Conceptual.IsolatedStorage#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source.cs#1)]
 [!code-vb[Conceptual.IsolatedStorage#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>  
- [Yalıtılmış Depolama](../../../docs/standard/io/isolated-storage.md)
