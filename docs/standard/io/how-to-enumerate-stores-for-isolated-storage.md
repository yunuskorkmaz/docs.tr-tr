---
title: "Nasıl yapılır: Yalıtılmış Depolama için Depoları Numaralandırma"
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
- enumerating stores
- data storage using isolated storage, enumerating stores
- storing data using isolated storage, enumerating stores
- stores, enumerating
- isolated storage, enumerating stores
- data stores, enumerating
ms.assetid: 0fcf279a-f241-48f0-8034-2e3d331f1fcb
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8f8863f1d8b3c7f4ed8f65f8f8eb3e8af51b0405
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-enumerate-stores-for-isolated-storage"></a>Nasıl yapılır: Yalıtılmış Depolama için Depoları Numaralandırma
Geçerli kullanıcı için tüm yalıtılmış depoları kullanarak numaralandırabilir <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType> statik yöntemi. Bu yöntem alır bir <xref:System.IO.IsolatedStorage.IsolatedStorageScope> değeri ve döndürür bir <xref:System.IO.IsolatedStorage.IsolatedStorageFile> Numaralandırıcı. Depoları numaralandırma için bilmeniz gereken <xref:System.Security.Permissions.IsolatedStorageFilePermission> belirtir izni <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> değeri. Çağırırsanız <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> yöntemiyle <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> değer, bir dizi döndürür <xref:System.IO.IsolatedStorage.IsolatedStorageFile> geçerli kullanıcı için tanımlanan nesneleri.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde, kullanıcı ve derlemeye göre yalıtılmış, birkaç dosyaları oluşturur ve bu dosyaları kullanarak alır bir mağaza edinir <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> yöntemi.  
  
 [!code-csharp[Conceptual.IsolatedStorage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source2.cs#2)]
 [!code-vb[Conceptual.IsolatedStorage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 [Yalıtılmış Depolama](../../../docs/standard/io/isolated-storage.md)
