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
ms.openlocfilehash: 83e8c800dc74d9689f1bfdb506a6b454e87b36ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75707876"
---
# <a name="how-to-create-files-and-directories-in-isolated-storage"></a>Nasıl yapılır: Yalıtılmış Depolamada Dosya ve Dizinler Oluşturma
Yalıtılmış bir depo elde ettikten sonra, veri depolamak için dizinler ve dosyalar oluşturabilirsiniz. Bir mağaza içinde, dosya ve dizin adları sanal dosya sisteminin köküne göre belirtilir.  
  
 Dizin oluşturmak için örnek <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType> yöntemini kullanın. Var olmayan bir dizinin alt dizinini belirtirseniz, her iki dizin oluşturulur. Zaten var olan bir dizini belirtirseniz, yöntem dizin oluşturmadan döndürür ve özel durum atılmaz. Ancak, geçersiz karakterler içeren bir dizin adı belirtirseniz, bir <xref:System.IO.IsolatedStorage.IsolatedStorageException> özel durum atılır.  
  
 Dosya oluşturmak için <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType> yöntemi kullanın.  
  
 Windows işletim sisteminde, yalıtılmış depolama dosyası ve dizin adları büyük/küçük harf duyarsızdır. Diğer bir tanesi, adlı `ThisFile.txt`bir dosya oluşturur ve `THISFILE.TXT`ardından başka bir dosya oluşturursanız, yalnızca bir dosya oluşturulur. Dosya adı, orijinal kasasını görüntü amacıyla tutar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, yalıtılmış bir depoda dosyaların ve dizinlerin nasıl oluşturulup oluşturulabildiğini göstermektedir.  
  
 [!code-csharp[Conceptual.IsolatedStorage#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source.cs#1)]
 [!code-vb[Conceptual.IsolatedStorage#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>
- [Yalıtılmış Depolama](../../../docs/standard/io/isolated-storage.md)
