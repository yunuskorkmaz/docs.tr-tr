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
ms.openlocfilehash: 6b1e8e651fd8e18c79dd629c154fb6c4d74243e3
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75707833"
---
# <a name="how-to-delete-stores-in-isolated-storage"></a>Nasıl yapılır: Yalıtılmış Depolamadaki Depoları Silme
<xref:System.IO.IsolatedStorage.IsolatedStorageFile> sınıfı yalıtılmış depolama dosyalarını silmek için iki yöntem sunar:  
  
- <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> örnek yöntemi herhangi bir bağımsız değişken almaz ve bunu çağıran mağazayı siler. Bu işlem için izin gerekli değildir. Mağazaya erişebilen tüm kodlar, içindeki verilerin herhangi birini veya tümünü silebilir.  
  
- Statik yöntem <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> numaralandırma değerini alır ve kodu çalıştıran kullanıcının tüm depolarını siler. Bu işlem, <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> değeri için <xref:System.Security.Permissions.IsolatedStorageFilePermission> izni gerektirir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, statik ve örnek <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> yöntemlerinin kullanımını gösterir. Sınıfı iki depo edinir; biri Kullanıcı ve derleme için yalıtılmıştır ve diğeri Kullanıcı, etki alanı ve derleme için yalıtılmıştır. Kullanıcı, etki alanı ve derleme deposu daha sonra yalıtılmış depolama dosyasının <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> yöntemi çağırarak silinir `isoStore1`. Sonra, Kullanıcı için kalan tüm depolar <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29>statik yöntem çağırarak silinir.  
  
 [!code-cpp[Conceptual.IsolatedStorage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.IsolatedStorage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source3.cs#3)]
 [!code-vb[Conceptual.IsolatedStorage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source3.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [Yalıtılmış Depolama](../../../docs/standard/io/isolated-storage.md)
