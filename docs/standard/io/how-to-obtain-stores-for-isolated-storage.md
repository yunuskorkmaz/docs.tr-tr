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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75706937"
---
# <a name="how-to-obtain-stores-for-isolated-storage"></a>Nasıl yapılır: Yalıtılmış Depolama için Depoları Alma
Yalıtılmış bir depo, veri bölmesi içindeki sanal bir dosya sistemini ortaya çıkarır. Sınıf, <xref:System.IO.IsolatedStorage.IsolatedStorageFile> yalıtılmış bir depoyla etkileşim kurmak için bir dizi yöntem sağlar. Mağazalar oluşturmak ve <xref:System.IO.IsolatedStorage.IsolatedStorageFile> almak için üç statik yöntem sağlar:  
  
- <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>kullanıcı ve derleme tarafından yalıtılmış depolama yı döndürür.  
  
- <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>etki alanı ve derleme tarafından yalıtılmış depolama döndürür.  
  
     Her iki yöntem de çağrıldıkları koda ait bir depoalır.  
  
- Statik yöntem, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> kapsam parametrelerinin bir birleşimini geçirerek belirtilen yalıtılmış bir depo döndürür.  
  
 Aşağıdaki kod, kullanıcı, derleme ve etki alanı tarafından yalıtılmış bir depodöndürür.  
  
 [!code-cpp[Conceptual.IsolatedStorage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#6)]
 [!code-csharp[Conceptual.IsolatedStorage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#6)]
 [!code-vb[Conceptual.IsolatedStorage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#6)]  
  
 Bir mağazanın <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> dolaşımdaki bir kullanıcı profiliyle dolaşması gerektiğini belirtmek için yöntemi kullanabilirsiniz. Bu nasıl ayarlanabilenayrıntılar [için, Yalıtım Türleri'ne](../../../docs/standard/io/types-of-isolation.md)bakın.  
  
 Farklı derlemeler içinden elde edilen yalıtılmış mağazalar, varsayılan olarak, farklı mağazalardır. <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> Yöntemin parametrelerinde derleme veya etki alanı kanıtgeçerek farklı bir derleme veya etki alanı deposuerişebilirsiniz. Bu, uygulama etki alanı kimliğine göre yalıtılmış depolama ya da depolama erişim izni gerektirir. Daha fazla bilgi <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> için yöntemin aşırı yüklenir.  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>ve <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> yöntemler bir <xref:System.IO.IsolatedStorage.IsolatedStorageFile> nesneyi döndürer. Durumunuziçin en uygun yalıtım türünün olduğuna karar vermenize yardımcı olmak için [bkz.](../../../docs/standard/io/types-of-isolation.md) Yalıtılmış bir depolama dosyası nesneniz olduğunda, dosyaları ve dizinleri okumak, yazmak, oluşturmak ve silmek için yalıtılmış depolama yöntemlerini kullanabilirsiniz.  
  
 Kodun, mağazanın kendisini almak <xref:System.IO.IsolatedStorage.IsolatedStorageFile> için yeterli erişimi olmayan bir nesneyi koda geçirmesini engelleyen bir mekanizma yoktur. Etki alanı ve derleme kimlikleri ve yalıtılmış depolama izinleri yalnızca <xref:System.IO.IsolatedStorage.IsolatedStorage> bir nesneye <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>başvuru <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> elde edildiğinde (genellikle , veya yöntemde) denetlenir. Nesnelere <xref:System.IO.IsolatedStorage.IsolatedStorageFile> yapılan başvuruları korumak, bu nedenle, bu başvuruları kullanan kodun sorumluluğundadır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, kullanıcı ve derleme tarafından yalıtılmış bir depo elde eden bir sınıfın basit bir örneğini sağlar. Kod, <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Domain?displayProperty=nameWithType> <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> yöntemin geçtiği bağımsız değişkenlere eklenerek kullanıcı, etki alanı ve derleme tarafından yalıtılmış bir depoyu almak için değiştirilebilir.  
  
 Kodu çalıştırdıktan sonra, komut satırına **StoreAdm /LIST** yazarak bir mağaza oluşturulduğunu doğrulayabilirsiniz. Bu, [Yalıtılmış Depolama aracını (Storeadm.exe)](../../../docs/framework/tools/storeadm-exe-isolated-storage-tool.md) çalıştırıyor ve kullanıcı için tüm geçerli yalıtılmış depoları listeler.  
  
 [!code-cpp[Conceptual.IsolatedStorage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#7)]
 [!code-csharp[Conceptual.IsolatedStorage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#7)]
 [!code-vb[Conceptual.IsolatedStorage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#7)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- <xref:System.IO.IsolatedStorage.IsolatedStorageScope>
- [Yalıtılmış Depolama](../../../docs/standard/io/isolated-storage.md)
- [Yalıtım Türleri](../../../docs/standard/io/types-of-isolation.md)
- [.NET’te bütünleştirilmiş kodlar](../assembly/index.md)
