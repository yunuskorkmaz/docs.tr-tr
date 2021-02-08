---
description: 'Daha fazla bilgi edinin: nasıl yapılır: yalıtılmış depolama için depoları numaralandırma'
title: 'Nasıl yapılır: Yalıtılmış Depolama için Depoları Numaralandırma'
ms.date: 03/30/2017
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
ms.openlocfilehash: f1acd6eaac5e81e9ea7a63b0eac4ef5a4a70efde
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99775623"
---
# <a name="how-to-enumerate-stores-for-isolated-storage"></a>Nasıl yapılır: Yalıtılmış Depolama için Depoları Numaralandırma

Statik yöntemi kullanarak geçerli kullanıcı için yalıtılmış tüm depoları sıralayabilirsiniz  <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType> . Bu yöntem bir <xref:System.IO.IsolatedStorage.IsolatedStorageScope> değer alır ve bir <xref:System.IO.IsolatedStorage.IsolatedStorageFile> Numaralandırıcı döndürür. Depoları listelemek için, <xref:System.Security.Permissions.IsolatedStorageFilePermission> değeri belirten izninizin olması gerekir <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> . <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A>Yöntemini değeri ile çağırırsanız <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> , <xref:System.IO.IsolatedStorage.IsolatedStorageFile> geçerli kullanıcı için tanımlanan nesne dizisini döndürür.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod örneği, Kullanıcı ve derleme tarafından yalıtılmış bir mağaza edinir, birkaç dosya oluşturur ve yöntemini kullanarak bu dosyaları alır <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> .  
  
 [!code-csharp[Conceptual.IsolatedStorage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source2.cs#2)]
 [!code-vb[Conceptual.IsolatedStorage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [Yalıtılmış depolama](isolated-storage.md)
