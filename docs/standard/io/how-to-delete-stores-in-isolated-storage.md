---
description: 'Şu konuda daha fazla bilgi edinin: nasıl yapılır: Yalıtılmış Depolamadaki Depoları Silme'
title: 'Nasıl yapılır: Yalıtılmış Depolamadaki Depoları Silme'
ms.date: 03/30/2017
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
ms.openlocfilehash: 3e454492c6a6e24feb57acf20afe1073d7ffbb4e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99775649"
---
# <a name="how-to-delete-stores-in-isolated-storage"></a>Nasıl yapılır: Yalıtılmış Depolamadaki Depoları Silme

<xref:System.IO.IsolatedStorage.IsolatedStorageFile>Sınıfı yalıtılmış depolama dosyalarını silmek için iki yöntem sunar:  
  
- Örnek yöntemi <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> herhangi bir bağımsız değişken almaz ve bunu çağıran depoyu siler. Bu işlem için izin gerekli değildir. Mağazaya erişebilen tüm kodlar, içindeki verilerin herhangi birini veya tümünü silebilir.  
  
- Statik yöntem, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> numaralandırma değerini alır ve kodu çalıştıran kullanıcının tüm depolarını siler. Bu işlem <xref:System.Security.Permissions.IsolatedStorageFilePermission> değer için izin gerektiriyor <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> .  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod örneği, statik ve örnek yöntemlerinin kullanımını gösterir <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> . Sınıfı iki depo edinir; biri Kullanıcı ve derleme için yalıtılmıştır ve diğeri Kullanıcı, etki alanı ve derleme için yalıtılmıştır. Kullanıcı, etki alanı ve derleme deposu daha sonra <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> yalıtılmış depolama dosyasının yöntemi çağırarak silinir  `isoStore1` . Ardından, kullanıcının tüm geri kalan depoları statik yöntem çağırarak silinir <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> .  
  
 [!code-cpp[Conceptual.IsolatedStorage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.IsolatedStorage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source3.cs#3)]
 [!code-vb[Conceptual.IsolatedStorage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source3.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [Yalıtılmış depolama](isolated-storage.md)
