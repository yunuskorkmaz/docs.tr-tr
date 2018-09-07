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
ms.openlocfilehash: 1e2f87bfe1e3e7f3a1c8135c047b25a998793453
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44084076"
---
# <a name="how-to-obtain-stores-for-isolated-storage"></a>Nasıl yapılır: Yalıtılmış Depolama için Depoları Alma
Bir yalıtılmış depolama bir veri bölmesi sanal dosya sisteminde kullanıma sunar. <xref:System.IO.IsolatedStorage.IsolatedStorageFile> Sınıfı bir dizi bir yalıtılmış depolama ile etkileşim kurmak için yöntem sağlar. Oluşturma ve depoları almak için <xref:System.IO.IsolatedStorage.IsolatedStorageFile> üç statik yöntemler sağlar:  
  
-   <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> Kullanıcı ve derlemeye göre yalıtılmış depolama döndürür.  
  
-   <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A> etki alanı ve derlemeye göre yalıtılır depolama döndürür.  
  
     Her iki yöntem içinden çağrılır koda ait bir depolama alın.  
  
-   Statik yöntem <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> kapsam parametre birleşimi geçirerek belirtilen bir yalıtılmış depolama döndürür.  
  
 Aşağıdaki kod, kullanıcı, derleme ve etki alanı tarafından izole edilmiş bir depo döndürür.  
  
 [!code-cpp[Conceptual.IsolatedStorage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#6)]
 [!code-csharp[Conceptual.IsolatedStorage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#6)]
 [!code-vb[Conceptual.IsolatedStorage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#6)]  
  
 Kullanabileceğiniz <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> gezici kullanıcı profili ile mağaza Dolaşımda olması belirtmek için yöntemi. Bu nasıl oluşturulacağı hakkında daha fazla bilgi için bkz: [türleri, yalıtım](../../../docs/standard/io/types-of-isolation.md).  
  
 Farklı bütünleştirilmiş kodlarında alınan yalıtılmış depoları, varsayılan olarak, farklı mağazalarda olur. Derleme veya etki alanı kanıt parametrelerinde olarak geçirerek farklı bir derleme veya etki alanının depoya erişebilir <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> yöntemi. Bu, uygulama etki alanı kimliği tarafından yalıtılmış depolamaya erişmek için izin gerekiyor. Daha fazla bilgi için <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> yöntemi aşırı yüklemeleri.  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, Ve <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> yöntemleri döndürür bir <xref:System.IO.IsolatedStorage.IsolatedStorageFile> nesne. Hangi yalıtım türü durumunuza en uygun olduğuna karar vermenize yardımcı olmak için bkz: [türleri, yalıtım](../../../docs/standard/io/types-of-isolation.md). Bir yalıtılmış depolama dosyası nesne varsa, okuma, yazma, oluşturmak için yalıtılmış depolama yöntemleri kullanın ve dosya ve dizinleri silin.  
  
 Kod geçirme dan engelleyen bir mekanizma bulunmamaktadır bir <xref:System.IO.IsolatedStorage.IsolatedStorageFile> , kod nesne deposu almak için yeterli erişimi yok. Etki alanı ve derlemeye kimlikleri ve yalıtılmış depolama izinleri yalnızca başvuru olduğunda denetlenir bir <xref:System.IO.IsolatedStorage.IsolatedStorage> nesnesi elde edilir, normalde <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, veya <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> yöntemi. Başvurular koruma <xref:System.IO.IsolatedStorage.IsolatedStorageFile> nesnedir, bu nedenle, sorumluluğu bu başvuruları kullanan kod.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, kullanıcı ve derlemeye göre yalıtılır mağaza alma bir sınıfın basit bir örnek sağlar. Kod ekleyerek kullanıcı, etki alanı ve derlemeye göre yalıtılır bir depo almak için değiştirilebilir <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Domain?displayProperty=nameWithType> bağımsız değişkenler için <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> yöntemi geçirir.  
  
 Kod çalıştırdıktan sonra bir deposuna yazarak oluşturulduğunu doğrulayabilirsiniz **StoreAdm/List** komut satırına. Bu çalıştırır [yalıtılmış depolama aracı (Storeadm.exe)](../../../docs/framework/tools/storeadm-exe-isolated-storage-tool.md) ve tüm yalıtılmış geçerli kullanıcı için depolar listelenmektedir.  
  
 [!code-cpp[Conceptual.IsolatedStorage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#7)]
 [!code-csharp[Conceptual.IsolatedStorage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#7)]
 [!code-vb[Conceptual.IsolatedStorage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#7)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
- <xref:System.IO.IsolatedStorage.IsolatedStorageScope>  
- [Yalıtılmış Depolama](../../../docs/standard/io/isolated-storage.md)  
- [Yalıtım Türleri](../../../docs/standard/io/types-of-isolation.md)  
- [Ortak Dil Çalışma Zamanı Modülündeki Bütünleştirilmiş Kodlar](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
