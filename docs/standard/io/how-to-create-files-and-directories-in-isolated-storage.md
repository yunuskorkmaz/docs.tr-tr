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
ms.openlocfilehash: d5e086e77ab6309fa0757ef32b620e0fdbc1f627
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413048"
---
# <a name="how-to-create-files-and-directories-in-isolated-storage"></a>Nasıl yapılır: Yalıtılmış Depolamada Dosya ve Dizinler Oluşturma
Yalıtılmış bir mağaza elde ettikten sonra, verileri depolamak için dizin ve dosya oluşturabilirsiniz. Bir mağaza içinde, dosya ve Dizin adları, sanal dosya sisteminin köküne göre belirtilir.  
  
 Bir dizin oluşturmak için <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType> örnek yöntemi kullanın. Mevcut olmayan bir dizinin alt dizinini belirtirseniz, her iki dizin de oluşturulur. Zaten var olan bir dizin belirtirseniz, yöntem bir dizin oluşturmadan geri döner ve hiçbir özel durum oluşturulmaz. Ancak, geçersiz karakterler içeren bir dizin adı belirtirseniz, bir <xref:System.IO.IsolatedStorage.IsolatedStorageException> özel durum oluşturulur.  
  
 Bir dosya oluşturmak için <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType> yöntemini kullanın.  
  
 Windows işletim sisteminde, yalıtılmış depolama dosyası ve Dizin adları büyük/küçük harfe duyarlıdır. Diğer bir deyişle, adlı bir dosya oluşturup `ThisFile.txt` daha sonra adlı başka bir dosya oluşturursanız `THISFILE.TXT` , yalnızca bir dosya oluşturulur. Dosya adı, görüntü amaçlarıyla orijinal büyük küçük harf durumunu korur.  

 Yalıtılmış depolama dosyası oluşturma <xref:System.IO.IsolatedStorage.IsolatedStorageException> yolu, mevcut olmayan bir dizin içeriyorsa, bir oluşturur.
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, yalıtılmış bir depoda dosyaların ve dizinlerin nasıl oluşturulacağını göstermektedir.  
  
 [!code-csharp[Conceptual.IsolatedStorage#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source.cs#1)]
 [!code-vb[Conceptual.IsolatedStorage#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>
- [Yalıtılmış depolama](isolated-storage.md)
