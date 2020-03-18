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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708121"
---
# <a name="how-to-anticipate-out-of-space-conditions-with-isolated-storage"></a>Nasıl yapılır: Yalıtılmış Depolama ile Alan Dolu Koşullarını Öngörme

Yalıtılmış depolama kullanan kod, yalıtılmış depolama dosyalarının ve dizinlerinin bulunduğu veri bölmesi için en büyük boyutu belirten bir [kotayla](../../../docs/standard/io/isolated-storage.md#quotas) sınırlandırılır. Kota güvenlik ilkesi tarafından tanımlanır ve yöneticiler tarafından yapılandırılabilir. Veri yazmaya çalıştığınızda izin verilen en büyük boyut <xref:System.IO.IsolatedStorage.IsolatedStorageException> aşılırsa, bir özel durum atılır ve işlem başarısız olur. Bu, veri depolama alanı dolu olduğundan uygulamanın istekleri reddetmesine neden olabilecek kötü amaçlı hizmet reddi saldırılarını önlemeye yardımcı olur.

Belirli <xref:System.IO.IsolatedStorage.IsolatedStorage> bir yazma denemesinin bu nedenle başarısız olma olasılığının yüksek olup olmadığını belirlemenize yardımcı olmak için, sınıf üç salt okunur özelliği sağlar: <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorage.UsedSize%2A>ve <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A>. Bu özellikleri, depoya yazmanın deponun izin verilen maksimum boyutunun aşılmasına neden olup olmayacağını belirlemek için kullanabilirsiniz. Yalıtılmış depolamaya aynı anda erişilebileni unutmayın; bu nedenle, kalan depolama miktarını hesapladiğinizde, depolama alanı mağazaya yazmaya çalıştığınızzaman tüketilebilir. Ancak, kullanılabilir depolama alanının üst sınırına ulaşılmak üzere olup olmadığını belirlemeye yardımcı olmak için mağazanın en büyük boyutunu kullanabilirsiniz.

Özellik <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A> düzgün çalışması için montaj kanıt bağlıdır. Bu nedenle, bu özelliği yalnızca <xref:System.IO.IsolatedStorage.IsolatedStorageFile> <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, , <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>veya <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> yöntem kullanılarak oluşturulan nesnelerüzerinde almalısınız. <xref:System.IO.IsolatedStorage.IsolatedStorageFile>başka bir şekilde oluşturulan nesneler (örneğin, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> yöntemden döndürülen nesneler) doğru bir maksimum boyutu döndürmez.

## <a name="example"></a>Örnek

Aşağıdaki kod örneği yalıtılmış bir depo alır, birkaç dosya <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A> oluşturur ve özelliği alır. Kalan alan baytolarak bildirilir.

[!code-cpp[Conceptual.IsolatedStorage#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source7.cpp#8)]
[!code-csharp[Conceptual.IsolatedStorage#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source7.cs#8)]
[!code-vb[Conceptual.IsolatedStorage#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source7.vb#8)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [Yalıtılmış Depolama](../../../docs/standard/io/isolated-storage.md)
- [Nasıl yapılır: Yalıtılmış Depolama için Depoları Alma](../../../docs/standard/io/how-to-obtain-stores-for-isolated-storage.md)
