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
ms.openlocfilehash: 9b99803970b205e3dbbb1d78c9bdaf0fefa73a04
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33575586"
---
# <a name="how-to-anticipate-out-of-space-conditions-with-isolated-storage"></a>Nasıl yapılır: Yalıtılmış Depolama ile Alan Dolu Koşullarını Öngörme
Yalıtılmış depolama kullanan kodu kısıtlı tarafından bir [kota](../../../docs/standard/io/isolated-storage.md#quotas) , veri bölme yalıtılmış depolama dosyaları ve dizinleri mevcut en büyük boyutunu belirtir. Kota güvenlik ilkesi tarafından tanımlanır ve yöneticiler tarafından yapılandırılabilir. Veri yazma çalıştığınızda boyutu aşıldı izin verilen en fazla ise bir <xref:System.IO.IsolatedStorage.IsolatedStorageException> özel durumu oluşur ve işlem başarısız olur. Bu veri depolama alanı dolu olduğundan isteği reddedecek şekilde uygulama neden olabilecek kötü amaçlı hizmet reddi saldırılarını önlemeye yardımcı olur.  
  
 Verilen yazma girişimi büyük olasılıkla bu nedenle, başarısız olup olmadığını belirlemek için <xref:System.IO.IsolatedStorage.IsolatedStorage> sınıfı üç salt okunur özellikler sağlar: <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorage.UsedSize%2A>, ve <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A>. Bu özellikleri deposuna yazma aşılmış için depolama boyutu izin verilen maksimum neden olup olmadığını belirlemek için kullanabilirsiniz. Yalıtılmış Depolama unutmayın aynı anda erişilebileceği; Bu nedenle, kalan depolama miktarını işlem, depolama alanı deposuna yazmak için deneyin zamana göre kullanılabilecek. Ancak, deponun en büyük boyutu kullanılabilir depolama alanı üst sınırını ulaşılmak üzere olup olmadığını belirlemek için kullanabilirsiniz.  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A> Özelliği düzgün çalışması için derlemesinden kanıt bağlıdır. Bu nedenle, yalnızca bu özellik alma <xref:System.IO.IsolatedStorage.IsolatedStorageFile> kullanılarak oluşturulan nesneler <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, veya <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> yöntemi. <xref:System.IO.IsolatedStorage.IsolatedStorageFile> herhangi bir yolla oluşturulan nesneleri (örneğin, döndürülen nesneleri <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> yöntemi) doğru en büyük boyutu döndürmez.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde bir yalıtılmış depolamada alır, birkaç dosyaları oluşturur ve alır <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A> özelliği. Kalan alanı bayt olarak bildirilir.  
  
 [!code-cpp[Conceptual.IsolatedStorage#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source7.cpp#8)]
 [!code-csharp[Conceptual.IsolatedStorage#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source7.cs#8)]
 [!code-vb[Conceptual.IsolatedStorage#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source7.vb#8)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 [Yalıtılmış Depolama](../../../docs/standard/io/isolated-storage.md)  
 [Nasıl yapılır: Yalıtılmış Depolama için Depoları Alma](../../../docs/standard/io/how-to-obtain-stores-for-isolated-storage.md)
