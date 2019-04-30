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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f14259afe4ee296d930b042d9e9ef069a81e65f9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61751780"
---
# <a name="how-to-enumerate-stores-for-isolated-storage"></a>Nasıl yapılır: Yalıtılmış Depolama için Depoları Numaralandırma
Geçerli kullanıcı için tüm yalıtılmış depoları kullanarak numaralandırabilirsiniz <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType> statik yöntem. Bu yöntem bir <xref:System.IO.IsolatedStorage.IsolatedStorageScope> döndürür ve değeri bir <xref:System.IO.IsolatedStorage.IsolatedStorageFile> Numaralandırıcı. Depoları numaralandırma için olmalıdır <xref:System.Security.Permissions.IsolatedStorageFilePermission> belirten izni <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> değeri. Eğer <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> yöntemiyle <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> değer dizisi döndürür <xref:System.IO.IsolatedStorage.IsolatedStorageFile> geçerli kullanıcı için tanımlanan nesneleri.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, kullanıcı ve derlemeye göre yalıtılır, birkaç dosya oluşturur ve bu dosyaları kullanarak alır bir depo alır <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> yöntemi.  
  
 [!code-csharp[Conceptual.IsolatedStorage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source2.cs#2)]
 [!code-vb[Conceptual.IsolatedStorage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [Yalıtılmış Depolama](../../../docs/standard/io/isolated-storage.md)
