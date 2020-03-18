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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75707534"
---
# <a name="how-to-enumerate-stores-for-isolated-storage"></a>Nasıl yapılır: Yalıtılmış Depolama için Depoları Numaralandırma
<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType> Statik yöntemi kullanarak geçerli kullanıcı için tüm yalıtılmış depoları sayısalatabilirsiniz. Bu yöntem <xref:System.IO.IsolatedStorage.IsolatedStorageScope> bir değer <xref:System.IO.IsolatedStorage.IsolatedStorageFile> alır ve bir sayısallaştırıcı döndürür. Depoları sayısallandırmak için, <xref:System.Security.Permissions.IsolatedStorageFilePermission> <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> değeri belirten izne sahip olmalısınız. <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> Yöntemi <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> değeri olan bir yöntem olarak çağırırsanız, geçerli kullanıcı için tanımlanan bir dizi <xref:System.IO.IsolatedStorage.IsolatedStorageFile> nesne döndürür.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, kullanıcı ve derleme tarafından yalıtılmış bir depo alır, birkaç dosya <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> oluşturur ve yöntemi kullanarak bu dosyaları alır.  
  
 [!code-csharp[Conceptual.IsolatedStorage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source2.cs#2)]
 [!code-vb[Conceptual.IsolatedStorage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [Yalıtılmış Depolama](../../../docs/standard/io/isolated-storage.md)
