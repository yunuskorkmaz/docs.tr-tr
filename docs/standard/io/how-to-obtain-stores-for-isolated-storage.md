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
ms.openlocfilehash: 7104ba665f60c2d55217a2d8628c85f6e469ad6f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706937"
---
# <a name="how-to-obtain-stores-for-isolated-storage"></a>Nasıl yapılır: Yalıtılmış Depolama için Depoları Alma
Yalıtılmış bir mağaza, bir veri bölmesi içinde sanal bir dosya sistemi sunar. <xref:System.IO.IsolatedStorage.IsolatedStorageFile> sınıfı, yalıtılmış bir mağaza ile etkileşim kurmak için çeşitli yöntemler sağlar. Mağaza oluşturmak ve almak için <xref:System.IO.IsolatedStorage.IsolatedStorageFile> üç statik yöntem sağlar:  
  
- <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, Kullanıcı ve derleme tarafından yalıtılmış depolama döndürür.  
  
- <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, etki alanı ve derleme tarafından yalıtılmış depolama döndürür.  
  
     Her iki yöntem de çağrıldıkları koda ait bir depoyu alır.  
  
- Statik yöntem <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>, kapsam parametrelerinin birleşimine geçerek belirtilen yalıtılmış bir depoyu döndürür.  
  
 Aşağıdaki kod, Kullanıcı, derleme ve etki alanı tarafından yalıtılmış bir depo döndürür.  
  
 [!code-cpp[Conceptual.IsolatedStorage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#6)]
 [!code-csharp[Conceptual.IsolatedStorage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#6)]
 [!code-vb[Conceptual.IsolatedStorage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#6)]  
  
 Bir deponun bir dolaşım kullanıcı profiliyle dolaşımını belirtmek için <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> yöntemini kullanabilirsiniz. Bu ayarı ayarlama hakkında daha fazla bilgi için bkz. [yalıtım türleri](../../../docs/standard/io/types-of-isolation.md).  
  
 Farklı derlemelerin içinden alınan yalıtılmış depolar, varsayılan olarak farklı depolardır. <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> yönteminin parametrelerinde derleme veya etki alanı bulgusunda geçirerek, farklı bir derleme veya etki alanı deposuna erişebilirsiniz. Bu, uygulama etki alanı kimliğine göre yalıtılmış depolamaya erişmek için izin gerektirir. Daha fazla bilgi için <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> yöntemi aşırı yüklemeleri bölümüne bakın.  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>ve <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> yöntemleri bir <xref:System.IO.IsolatedStorage.IsolatedStorageFile> nesnesi döndürüyor. Hangi yalıtım türünün durumunuza en uygun olduğuna karar vermenize yardımcı olması için bkz. [yalıtım türleri](../../../docs/standard/io/types-of-isolation.md). Yalıtılmış bir depolama dosya nesneniz varsa, dosyaları ve dizinleri okumak, yazmak, oluşturmak ve silmek için yalıtılmış depolama yöntemlerini kullanabilirsiniz.  
  
 Kodun bir <xref:System.IO.IsolatedStorage.IsolatedStorageFile> nesnesini, deponun kendisini almak için yeterli erişimi olmayan koda geçirilmesini engelleyen bir mekanizma yoktur. Etki alanı ve derleme kimlikleri ve yalıtılmış depolama izinleri yalnızca, genellikle <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>veya <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> yönteminde bir <xref:System.IO.IsolatedStorage.IsolatedStorage> nesnesine başvuru elde edildiğinde denetlenir. <xref:System.IO.IsolatedStorage.IsolatedStorageFile> nesnelerine başvuruları korumak, bu nedenle bu başvuruları kullanan kodun sorumluluğundadır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, Kullanıcı ve derleme tarafından yalıtılmış bir depo elde eden bir sınıfa ilişkin basit bir örnek sağlar. Kod, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> yönteminin geçtiği bağımsız değişkenlere <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Domain?displayProperty=nameWithType> ekleyerek Kullanıcı, etki alanı ve derleme tarafından yalıtılmış bir depoyu almak üzere değiştirilebilir.  
  
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
