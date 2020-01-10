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
- quantity of isolated storage used
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
ms.openlocfilehash: 5666019e1a65880221261ef5ad704f82c37263b2
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708121"
---
# <a name="how-to-anticipate-out-of-space-conditions-with-isolated-storage"></a>Nasıl yapılır: Yalıtılmış Depolama ile Alan Dolu Koşullarını Öngörme

Yalıtılmış depolama kullanan kod, yalıtılmış depolama dosyalarının ve dizinlerinin mevcut olduğu veri bölmesi için en büyük boyutu belirten bir [Kota](../../../docs/standard/io/isolated-storage.md#quotas) ile kısıtlanır. Kota güvenlik ilkesi tarafından tanımlanır ve yöneticiler tarafından yapılandırılabilir. Veri yazmaya çalıştığınızda izin verilen en büyük boyut aşılırsa, <xref:System.IO.IsolatedStorage.IsolatedStorageException> bir özel durum oluşturulur ve işlem başarısız olur. Bu, veri depolama alanı doldurulduğundan uygulamanın istekleri reddetmesine neden olabilecek kötü amaçlı hizmet reddi saldırılarını önlemeye yardımcı olur.

Bu nedenle, belirli bir yazma denemesinin başarısız olup olmadığını belirlemenize yardımcı olmak için <xref:System.IO.IsolatedStorage.IsolatedStorage> sınıfı üç salt okunurdur özellikler sağlar: <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorage.UsedSize%2A>ve <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A>. Bu özellikleri, mağazaya yazmanın izin verilen en fazla depolama boyutunun aşılmasına neden olup olmayacağını anlamak için kullanabilirsiniz. Yalıtılmış depolamaya aynı anda erişildiğini aklınızda bulundurun; Bu nedenle, kalan depolama miktarını hesaplarken, depolama alanı mağazaya yazmayı denediğinizde tüketilebilir. Ancak, kullanılabilir depolama alanının üst sınırına ulaşılmaya ulaşılmadığını belirlemenize yardımcı olması için deponun en büyük boyutunu kullanabilirsiniz.

<xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A> özelliği, derlemenin düzgün şekilde çalışması için olan kanıta bağlıdır. Bu nedenle, bu özelliği yalnızca <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>veya <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> yöntemi kullanılarak oluşturulan <xref:System.IO.IsolatedStorage.IsolatedStorageFile> nesneler üzerinde almalısınız. başka herhangi bir şekilde oluşturulmuş nesneleri <xref:System.IO.IsolatedStorage.IsolatedStorageFile> (örneğin, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> yönteminden döndürülen nesneler), doğru en büyük boyutu döndürmez.

## <a name="example"></a>Örnek

Aşağıdaki kod örneği yalıtılmış bir depo edinir, birkaç dosya oluşturur ve <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A> özelliğini alır. Kalan alan bayt cinsinden raporlanır.

[!code-cpp[Conceptual.IsolatedStorage#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source7.cpp#8)]
[!code-csharp[Conceptual.IsolatedStorage#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source7.cs#8)]
[!code-vb[Conceptual.IsolatedStorage#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source7.vb#8)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [Yalıtılmış Depolama](../../../docs/standard/io/isolated-storage.md)
- [Nasıl yapılır: Yalıtılmış Depolama için Depoları Alma](../../../docs/standard/io/how-to-obtain-stores-for-isolated-storage.md)
