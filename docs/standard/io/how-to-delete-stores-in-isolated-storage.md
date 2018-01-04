---
title: "Nasıl yapılır: Yalıtılmış Depolamadaki Depoları Silme"
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
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3ae04deeb8d23b496a9111b0d4b5b68e12ac1439
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-delete-stores-in-isolated-storage"></a>Nasıl yapılır: Yalıtılmış Depolamadaki Depoları Silme
<xref:System.IO.IsolatedStorage.IsolatedStorageFile> Sınıfı yalıtılmış depolama dosyaları silmek için iki yöntem sunar:  
  
-   Örnek yöntemi <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> herhangi bir bağımsız değişken almaz ve çağırır deposu siler. Bu işlem için yok izinleri gereklidir. Deposuna erişebilecek herhangi bir kod tüm veriler içindeki silebilirsiniz.  
  
-   Statik yöntemi <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> geçen <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> numaralandırma değeri ve silme kod kullanan kullanıcı için tüm depolar. Bu işlem gerektirir <xref:System.Security.Permissions.IsolatedStorageFilePermission> izni <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> değeri.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde statik kullanımını ve örneği gösterilmektedir <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> yöntemleri. Sınıfın iki depoları alır; Kullanıcı ve derleme için yalıtılmış biridir ve diğer kullanıcı, etki alanı ve derleme için ayrı tutulur. Kullanıcı, etki alanı ve derleme deposu çağırarak ardından silinir <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> yalıtılmış depolama dosyasının yöntemini `isoStore1`. Ardından, kullanıcı için tüm kalan depolarını statik yöntemini çağırarak silinir <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29>.  
  
 [!code-cpp[Conceptual.IsolatedStorage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.IsolatedStorage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source3.cs#3)]
 [!code-vb[Conceptual.IsolatedStorage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source3.vb#3)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 [Yalıtılmış Depolama](../../../docs/standard/io/isolated-storage.md)
