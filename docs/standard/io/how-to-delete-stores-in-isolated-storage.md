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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75707833"
---
# <a name="how-to-delete-stores-in-isolated-storage"></a>Nasıl yapılır: Yalıtılmış Depolamadaki Depoları Silme
Sınıf, <xref:System.IO.IsolatedStorage.IsolatedStorageFile> yalıtılmış depolama dosyalarını siler için iki yöntem sağlar:  
  
- Örnek yöntem <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> herhangi bir bağımsız değişken almaz ve onu çağıran mağazayı siler. Bu işlem için izin gerekmez. Depoya erişebilen herhangi bir kod içindeki verileri veya tümünü silebilir.  
  
- Statik yöntem <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> numaralandırma değerini alır <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> ve kodu çalıştıran kullanıcı için tüm depoları siler. Bu <xref:System.Security.Permissions.IsolatedStorageFilePermission> <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> işlem, değer için izin gerektirir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği statik ve örnek <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> yöntemlerinin kullanımını gösterir. Sınıf iki mağaza alır; biri kullanıcı ve derleme için yalıtılmış, diğeri kullanıcı, etki alanı ve derleme için yalıtılmış. Kullanıcı, etki alanı ve montaj deposu sonra <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> yalıtılmış depolama `isoStore1`dosyasının yöntemini arayarak silinir. Daha sonra, kullanıcı için kalan tüm mağazalar <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29>statik yöntem çağırılarak silinir.  
  
 [!code-cpp[Conceptual.IsolatedStorage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.IsolatedStorage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source3.cs#3)]
 [!code-vb[Conceptual.IsolatedStorage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source3.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [Yalıtılmış Depolama](../../../docs/standard/io/isolated-storage.md)
