---
title: 'Nasıl yapılır: Yalıtılmış Depolama için Depoları Alma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- stores, obtaining
- storing data using isolated storage, obtaining stores
- isolated storage, obtaining stores
- data stores, obtaining
- data storage using isolated storage, obtaining stores
ms.assetid: fcb6b178-d526-47c4-b029-e946f880f9db
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d6fbc78c379951e05869a433875d057c49d44594
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70969253"
---
# <a name="how-to-obtain-stores-for-isolated-storage"></a>Nasıl yapılır: Yalıtılmış Depolama için Depoları Alma
Yalıtılmış bir mağaza, bir veri bölmesi içinde sanal bir dosya sistemi sunar. <xref:System.IO.IsolatedStorage.IsolatedStorageFile> Sınıfı yalıtılmış bir mağaza ile etkileşim kurmak için çeşitli yöntemler sağlar. Mağaza oluşturmak ve almak için üç <xref:System.IO.IsolatedStorage.IsolatedStorageFile> statik yöntem sağlar:  
  
- <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>Kullanıcı ve derleme tarafından yalıtılmış depolamayı döndürür.  
  
- <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>etki alanı ve derleme tarafından yalıtılmış depolamayı döndürür.  
  
     Her iki yöntem de çağrıldıkları koda ait bir depoyu alır.  
  
- Static yöntemi <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> , kapsam parametrelerinin bir birleşimi geçirerek belirtilen yalıtılmış bir depo döndürür.  
  
 Aşağıdaki kod, Kullanıcı, derleme ve etki alanı tarafından yalıtılmış bir depo döndürür.  
  
 [!code-cpp[Conceptual.IsolatedStorage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#6)]
 [!code-csharp[Conceptual.IsolatedStorage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#6)]
 [!code-vb[Conceptual.IsolatedStorage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#6)]  
  
 Bir deponun bir dolaşım <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> Kullanıcı profiliyle dolaşımını belirtmek için yöntemini kullanabilirsiniz. Bu ayarı ayarlama hakkında daha fazla bilgi için bkz. [yalıtım türleri](../../../docs/standard/io/types-of-isolation.md).  
  
 Farklı derlemelerin içinden alınan yalıtılmış depolar, varsayılan olarak farklı depolardır. Farklı bir derlemenin veya etki alanının deposuna, derleme veya etki alanı bulgusunda <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> metodun parametrelerini geçirerek erişebilirsiniz. Bu, uygulama etki alanı kimliğine göre yalıtılmış depolamaya erişmek için izin gerektirir. Daha fazla bilgi için bkz <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> . yöntem aşırı yüklemeleri.  
  
 , Ve yöntemleri bir nesnesini<xref:System.IO.IsolatedStorage.IsolatedStorageFile> döndürür. <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A> <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> Hangi yalıtım türünün durumunuza en uygun olduğuna karar vermenize yardımcı olması için bkz. [yalıtım türleri](../../../docs/standard/io/types-of-isolation.md). Yalıtılmış bir depolama dosya nesneniz varsa, dosyaları ve dizinleri okumak, yazmak, oluşturmak ve silmek için yalıtılmış depolama yöntemlerini kullanabilirsiniz.  
  
 Kodun, deponun kendisini almak için yeterli erişimi olmayan koda <xref:System.IO.IsolatedStorage.IsolatedStorageFile> bir nesne geçirilmesini engelleyen bir mekanizma yoktur. Etki alanı ve derleme kimlikleri ve <xref:System.IO.IsolatedStorage.IsolatedStorage> yalıtılmış depolama izinleri yalnızca <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, genellikle, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>veya <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> yönteminde bir nesne başvurusu elde edildiğinde denetlenir. Bu nedenle, <xref:System.IO.IsolatedStorage.IsolatedStorageFile> bu başvuruları kullanan kodun sorumluluğu, bu nedenle nesnelere başvuruları koruma.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, Kullanıcı ve derleme tarafından yalıtılmış bir depo elde eden bir sınıfa ilişkin basit bir örnek sağlar. Kod, <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Domain?displayProperty=nameWithType> <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> yöntemin geçirdiği bağımsız değişkenlere ekleyerek Kullanıcı, etki alanı ve derleme tarafından yalıtılmış bir depoyu almak üzere değiştirilebilir.  
  
 Kodu çalıştırdıktan sonra, komut satırına **Storeadm/List** yazarak bir deponun oluşturulduğunu doğrulayabilirsiniz. Bu, [yalıtılmış depolama aracı 'nı (Storeadmtm. exe)](../../../docs/framework/tools/storeadm-exe-isolated-storage-tool.md) çalıştırır ve Kullanıcı için tüm geçerli yalıtılmış depoları listeler.  
  
 [!code-cpp[Conceptual.IsolatedStorage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#7)]
 [!code-csharp[Conceptual.IsolatedStorage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#7)]
 [!code-vb[Conceptual.IsolatedStorage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#7)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- <xref:System.IO.IsolatedStorage.IsolatedStorageScope>
- [Yalıtılmış Depolama](../../../docs/standard/io/isolated-storage.md)
- [Yalıtım Türleri](../../../docs/standard/io/types-of-isolation.md)
- [.NET’te bütünleştirilmiş kodlar](../assembly/index.md)
