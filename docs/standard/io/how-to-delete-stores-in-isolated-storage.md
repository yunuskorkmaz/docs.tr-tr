---
title: 'Nasıl yapılır: Yalıtılmış Depolamadaki Depoları Silme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- stores, deleting
- data stores, deleting
- deleting stores
- removing stores
- isolated storage, deleting stores
- storing data using isolated storage, deleting stores
- data storage using isolated storage, deleting stores
ms.assetid: 3947e333-5af6-4601-b2f1-24d4d6129cf3
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 19a671cac609e79088956ecb4324ebb0a25fb941
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61751871"
---
# <a name="how-to-delete-stores-in-isolated-storage"></a>Nasıl yapılır: Yalıtılmış Depolamadaki Depoları Silme
<xref:System.IO.IsolatedStorage.IsolatedStorageFile> Sınıfı yalıtılmış depolama dosyalarının silinmesi için iki yöntem sunar:  
  
- Örnek yöntemini <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> herhangi bir bağımsız değişken almaz ve çağrı yaptığı deposunu siler. Bu işlem için gerekli izni yok. Depoya erişebilir herhangi bir kod, tüm verileri içine silebilirsiniz.  
  
- Statik yöntem <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> alan <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> numaralandırma değeri ve tüm depoları kodu çalıştıran kullanıcıyı siler. Bu işlem gerektiriyor <xref:System.Security.Permissions.IsolatedStorageFilePermission> izinlerini <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> değeri.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği statik kullanımını ve örnek gösterir <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> yöntemleri. Sınıfı iki deposu alır; bir kullanıcı ve derlemeye için yalıtılmış ve diğer kullanıcı, etki alanı ve derleme için ayrı tutulur. Kullanıcı, etki alanı ve derlemeye deponun çağırarak ardından silinir <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> yalıtılmış depolama dosyasına yöntemi `isoStore1`. Statik yöntemi çağırarak kullanıcı için tüm kalan depoları ardından silinir <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29>.  
  
 [!code-cpp[Conceptual.IsolatedStorage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.IsolatedStorage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source3.cs#3)]
 [!code-vb[Conceptual.IsolatedStorage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source3.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [Yalıtılmış Depolama](../../../docs/standard/io/isolated-storage.md)
