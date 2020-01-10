---
title: 'Nasıl yapılır: Yalıtılmış Depolama için Depoları Numaralandırma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- enumerating stores
- data storage using isolated storage, enumerating stores
- storing data using isolated storage, enumerating stores
- stores, enumerating
- isolated storage, enumerating stores
- data stores, enumerating
ms.assetid: 0fcf279a-f241-48f0-8034-2e3d331f1fcb
ms.openlocfilehash: 3ba38093e9e978c89cdb2bb7a584ed9e04c1096d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75707534"
---
# <a name="how-to-enumerate-stores-for-isolated-storage"></a>Nasıl yapılır: Yalıtılmış Depolama için Depoları Numaralandırma
<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType> static metodunu kullanarak geçerli kullanıcı için tüm yalıtılmış depoları numaralandırabilirsiniz. Bu yöntem bir <xref:System.IO.IsolatedStorage.IsolatedStorageScope> değeri alır ve <xref:System.IO.IsolatedStorage.IsolatedStorageFile> bir Numaralandırıcı döndürür. Depoları listelemek için, <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> değerini belirten <xref:System.Security.Permissions.IsolatedStorageFilePermission> izninizin olması gerekir. <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> yöntemini <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> değeriyle çağırırsanız, geçerli kullanıcı için tanımlanan <xref:System.IO.IsolatedStorage.IsolatedStorageFile> nesnelerinin bir dizisini döndürür.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, Kullanıcı ve derleme tarafından yalıtılmış bir mağaza edinir, birkaç dosya oluşturur ve <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> yöntemi kullanılarak bu dosyaları alır.  
  
 [!code-csharp[Conceptual.IsolatedStorage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source2.cs#2)]
 [!code-vb[Conceptual.IsolatedStorage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [Yalıtılmış Depolama](../../../docs/standard/io/isolated-storage.md)
