---
title: 'Nasıl yapılır: Yalıtılmış Depolama ile Alan Dolu Koşullarını Öngörme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data stores, quotas
- isolated storage, quotas
- quanitity of isolated storage used
- limit on isolated storage used
- stores, quotas
- stores, out of space conditions
- data storage using isolated storage, quotas
- storing data using isolated storage, quotas
- space remaining in isolated storage
- data stores, out of space conditions
- storing data using isolated storage, out of space conditions
- quotas for isolated storage
- isolated storage, out of space conditions
- data storage using isolated storage, out of space conditions
ms.assetid: e35d4535-3732-421e-b1a3-37412e036145
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 16b12a1ab274a63b8d190278d6312d36a61efe16
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44098387"
---
# <a name="how-to-anticipate-out-of-space-conditions-with-isolated-storage"></a>Nasıl yapılır: Yalıtılmış Depolama ile Alan Dolu Koşullarını Öngörme
Yalıtılmış depolama kullanan kodu je omezeno tarafından bir [kota](../../../docs/standard/io/isolated-storage.md#quotas) veri bölümünde yalıtılmış depolama dosyalarının ve dizinleri mevcut en büyük boyutu belirtir. Kota güvenlik ilkesi tarafından tanımlanır ve yöneticiler tarafından yapılandırılabilir. Veri yazma çalıştığınızda boyutu aşıldı izin verilen en fazla, bir <xref:System.IO.IsolatedStorage.IsolatedStorageException> özel durum oluştu ve işlem başarısız olur. Bu uygulama, veri depolama alanı dolu olduğundan istekleri reddetmek neden olabilecek kötü amaçlı hizmet reddi saldırılarını önlemeye yardımcı olur.  
  
 Belirtilen yazma girişimi, bu nedenle, başarısız olma olasılığı yüksek olup olmadığını belirlemenize yardımcı olmak üzere <xref:System.IO.IsolatedStorage.IsolatedStorage> sınıfı üç salt okunur özellikler sağlar: <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorage.UsedSize%2A>, ve <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A>. Bu özellikler, deposuna yazma olması deposunun boyutu izin verilen maksimum neden olup olmadığını belirlemek için kullanabilirsiniz. Yalıtılmış Depolama etkilenebileceğini eşzamanlı olarak erişilebilir; Bu nedenle, kalan depolama miktarını işlem, depolama alanını bir depoya yazmak için deneyin zamanına göre tüketilebilecek. Ancak, deponun en büyük boyutu kullanılabilir depolama alanı üst sınırına ulaşılmak üzere olup olmadığını belirlemenize yardımcı olması için kullanabilirsiniz.  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A> Özelliği düzgün şekilde çalışması için derlemeden kanıt bağlıdır. Bu nedenle, bu özellik yalnızca almalıdır <xref:System.IO.IsolatedStorage.IsolatedStorageFile> kullanılarak oluşturulan nesneleri <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, veya <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> yöntemi. <xref:System.IO.IsolatedStorage.IsolatedStorageFile> diğer herhangi bir yolla oluşturulan nesneleri (örneğin, öğesinden döndürülen nesneleri <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> yöntemi) doğru bir maksimum boyut döndürmez.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği bir yalıtılmış depolama alır, birkaç dosya oluşturur ve alır <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A> özelliği. Kalan alanı bayt olarak bildirilir.  
  
 [!code-cpp[Conceptual.IsolatedStorage#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source7.cpp#8)]
 [!code-csharp[Conceptual.IsolatedStorage#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source7.cs#8)]
 [!code-vb[Conceptual.IsolatedStorage#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source7.vb#8)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
- [Yalıtılmış Depolama](../../../docs/standard/io/isolated-storage.md)  
- [Nasıl yapılır: Yalıtılmış Depolama için Depoları Alma](../../../docs/standard/io/how-to-obtain-stores-for-isolated-storage.md)
