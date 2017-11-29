---
title: "Nasıl yapılır: Yalıtılmış Depolamada Dosya ve Dizinler Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8b8a48473bf9ac91b89657d00d27031255491353
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-files-and-directories-in-isolated-storage"></a>Nasıl yapılır: Yalıtılmış Depolamada Dosya ve Dizinler Oluşturma
Yalıtılmış depolamada aldıktan sonra dizinler ve dosyalar verilerini depolamak için oluşturabilirsiniz. Bir depo dosya ve dizin adları sanal dosya sisteminde kök göre belirtilir.  
  
 Bir dizin oluşturmak için kullanmak <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType> örnek yöntemi. Mevcut olmayan bir dizinin bir alt dizini belirtirseniz, her iki dizini oluşturulur. Zaten bir dizin belirtirseniz, bir dizin oluşturmadan yöntemi döndürür ve hiçbir özel durum oluşur. Ancak, bir dizin adı belirtirseniz, geçersiz karakterler içeren bir <xref:System.IO.IsolatedStorage.IsolatedStorageException> özel durumu oluşur.  
  
 Bir dosya oluşturmak için kullanın <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType> yöntemi.  
  
 Windows işletim sistemi, yalıtılmış depolama dosya ve dizin adları büyük küçük harfe duyarsızdır. Diğer bir deyişle, adında bir dosya oluşturursanız `ThisFile.txt`ve ardından adlı başka bir dosya oluşturun `THISFILE.TXT`, yalnızca bir dosya oluşturulur. Dosya adı, görüntüleme amaçlarıyla kendi özgün kasasını tutar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde dosyaları ve dizinleri yalıtılmış bir depolama alanına nasıl oluşturulacağını gösterir.  
  
 [!code-csharp[Conceptual.IsolatedStorage#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source.cs#1)]
 [!code-vb[Conceptual.IsolatedStorage#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>  
 [Yalıtılmış Depolama](../../../docs/standard/io/isolated-storage.md)
