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
ms.openlocfilehash: a08563b67239c679e3bc88876781508fd78bea75
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291844"
---
# <a name="how-to-obtain-stores-for-isolated-storage"></a>Nasıl yapılır: Yalıtılmış Depolama için Depoları Alma
Yalıtılmış bir mağaza, bir veri bölmesi içinde sanal bir dosya sistemi sunar. <xref:System.IO.IsolatedStorage.IsolatedStorageFile>Sınıfı yalıtılmış bir mağaza ile etkileşim kurmak için çeşitli yöntemler sağlar. Mağaza oluşturmak ve almak için <xref:System.IO.IsolatedStorage.IsolatedStorageFile> üç statik yöntem sağlar:  
  
- <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>Kullanıcı ve derleme tarafından yalıtılmış depolamayı döndürür.  
  
- <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>etki alanı ve derleme tarafından yalıtılmış depolamayı döndürür.  
  
     Her iki yöntem de çağrıldıkları koda ait bir depoyu alır.  
  
- Static yöntemi, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> kapsam parametrelerinin bir birleşimi geçirerek belirtilen yalıtılmış bir depo döndürür.  
  
 Aşağıdaki kod, Kullanıcı, derleme ve etki alanı tarafından yalıtılmış bir depo döndürür.  
  
 [!code-cpp[Conceptual.IsolatedStorage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#6)]
 [!code-csharp[Conceptual.IsolatedStorage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#6)]
 [!code-vb[Conceptual.IsolatedStorage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#6)]  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>Bir deponun bir dolaşım kullanıcı profiliyle dolaşımını belirtmek için yöntemini kullanabilirsiniz. Bu ayarı ayarlama hakkında daha fazla bilgi için bkz. [yalıtım türleri](types-of-isolation.md).  
  
 Farklı derlemelerin içinden alınan yalıtılmış depolar, varsayılan olarak farklı depolardır. Farklı bir derlemenin veya etki alanının deposuna, derleme veya etki alanı bulgusunda metodun parametrelerini geçirerek erişebilirsiniz <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> . Bu, uygulama etki alanı kimliğine göre yalıtılmış depolamaya erişmek için izin gerektirir. Daha fazla bilgi için bkz <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> . yöntem aşırı yüklemeleri.  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A> Ve <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> yöntemleri bir <xref:System.IO.IsolatedStorage.IsolatedStorageFile> nesnesini döndürür. Hangi yalıtım türünün durumunuza en uygun olduğuna karar vermenize yardımcı olması için bkz. [yalıtım türleri](types-of-isolation.md). Yalıtılmış bir depolama dosya nesneniz varsa, dosyaları ve dizinleri okumak, yazmak, oluşturmak ve silmek için yalıtılmış depolama yöntemlerini kullanabilirsiniz.  
  
 Kodun, <xref:System.IO.IsolatedStorage.IsolatedStorageFile> deponun kendisini almak için yeterli erişimi olmayan koda bir nesne geçirilmesini engelleyen bir mekanizma yoktur. Etki alanı ve derleme kimlikleri ve yalıtılmış depolama izinleri yalnızca <xref:System.IO.IsolatedStorage.IsolatedStorage> <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> , genellikle, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A> veya yönteminde bir nesne başvurusu elde edildiğinde denetlenir <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> . Bu nedenle, <xref:System.IO.IsolatedStorage.IsolatedStorageFile> Bu başvuruları kullanan kodun sorumluluğu, bu nedenle nesnelere başvuruları koruma.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, Kullanıcı ve derleme tarafından yalıtılmış bir depo elde eden bir sınıfa ilişkin basit bir örnek sağlar. Kod, <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Domain?displayProperty=nameWithType> yöntemin geçirdiği bağımsız değişkenlere ekleyerek Kullanıcı, etki alanı ve derleme tarafından yalıtılmış bir depoyu almak üzere değiştirilebilir <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> .  
  
 Kodu çalıştırdıktan sonra, komut satırına **Storeadm/List** yazarak bir deponun oluşturulduğunu doğrulayabilirsiniz. Bu, [yalıtılmış depolama aracı 'nı (Storeadmtm. exe)](../../framework/tools/storeadm-exe-isolated-storage-tool.md) çalıştırır ve Kullanıcı için tüm geçerli yalıtılmış depoları listeler.  
  
 [!code-cpp[Conceptual.IsolatedStorage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#7)]
 [!code-csharp[Conceptual.IsolatedStorage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#7)]
 [!code-vb[Conceptual.IsolatedStorage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#7)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- <xref:System.IO.IsolatedStorage.IsolatedStorageScope>
- [Yalıtılmış depolama](isolated-storage.md)
- [Yalıtım Türleri](types-of-isolation.md)
- [.NET’te bütünleştirilmiş kodlar](../assembly/index.md)
