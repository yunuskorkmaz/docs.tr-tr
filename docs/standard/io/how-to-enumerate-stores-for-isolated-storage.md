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
ms.openlocfilehash: 732f121e6b1977a960cab207f8d56cd2a551383c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291870"
---
# <a name="how-to-enumerate-stores-for-isolated-storage"></a>Nasıl yapılır: Yalıtılmış Depolama için Depoları Numaralandırma
Statik yöntemi kullanarak geçerli kullanıcı için yalıtılmış tüm depoları sıralayabilirsiniz <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType> . Bu yöntem bir <xref:System.IO.IsolatedStorage.IsolatedStorageScope> değer alır ve bir <xref:System.IO.IsolatedStorage.IsolatedStorageFile> Numaralandırıcı döndürür. Depoları listelemek için, <xref:System.Security.Permissions.IsolatedStorageFilePermission> değeri belirten izninizin olması gerekir <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> . <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A>Yöntemini değeri ile çağırırsanız <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> , <xref:System.IO.IsolatedStorage.IsolatedStorageFile> geçerli kullanıcı için tanımlanan nesne dizisini döndürür.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, Kullanıcı ve derleme tarafından yalıtılmış bir mağaza edinir, birkaç dosya oluşturur ve yöntemini kullanarak bu dosyaları alır <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> .  
  
 [!code-csharp[Conceptual.IsolatedStorage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source2.cs#2)]
 [!code-vb[Conceptual.IsolatedStorage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [Yalıtılmış depolama](isolated-storage.md)
