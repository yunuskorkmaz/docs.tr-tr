---
title: "Nasıl yapılır: Yalıtılmış Depolama için Depoları Alma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "19"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 61f183398c3f8c93ead965036e1edeb200dd8cb1
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-obtain-stores-for-isolated-storage"></a>Nasıl yapılır: Yalıtılmış Depolama için Depoları Alma
Yalıtılmış depolamada sanal dosya sistemi veri bölme içinde kullanıma sunar. <xref:System.IO.IsolatedStorage.IsolatedStorageFile> Sınıf, çeşitli bir yalıtılmış depolamada ile etkileşim için yöntemler sağlar. Oluşturmak ve depolar, almak için <xref:System.IO.IsolatedStorage.IsolatedStorageFile> üç statik yöntemler sağlar:  
  
-   <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>Kullanıcı ve derlemeye göre yalıtılmış depolama döndürür.  
  
-   <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>etki alanı ve derleme tarafından yalıtılır depolama döndürür.  
  
     Her iki yöntem, bunlar adlandırılır koduna ait bir depolama alın.  
  
-   Statik yöntemi <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> kapsam parametreleri bileşimini geçirerek belirtilen bir yalıtılmış depolamada döndürür.  
  
 Aşağıdaki kod, kullanıcı, derleme ve etki alanı tarafından ayrılmış bir depolama döndürür.  
  
 [!code-cpp[Conceptual.IsolatedStorage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#6)]
 [!code-csharp[Conceptual.IsolatedStorage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#6)]
 [!code-vb[Conceptual.IsolatedStorage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#6)]  
  
 Kullanabileceğiniz <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> yöntemi bir gezici kullanıcı profili ile bir depolama dolaşan belirtin. Bu nasıl oluşturulacağı hakkında daha fazla bilgi için bkz: [türleri, yalıtım](../../../docs/standard/io/types-of-isolation.md).  
  
 İçinde farklı derlemeler alınan yalıtılmış depolar, varsayılan olarak, farklı depoları etkilenir. Derleme veya etki alanı kanıt parametrelerinde içinde geçirerek farklı derleme veya etki alanının deposuna erişebilecek <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> yöntemi. Yalıtılmış Depolama uygulama etki alanı kimliği tarafından erişim izni gerektirir. Daha fazla bilgi için bkz: <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> yöntemi aşırı.  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, Ve <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> yöntemleri döndürür bir <xref:System.IO.IsolatedStorage.IsolatedStorageFile> nesnesi. Hangi yalıtım türü durumunuz için en uygun olan karar vermenize yardımcı olmak için bkz: [türleri, yalıtım](../../../docs/standard/io/types-of-isolation.md). Yalıtılmış depolama dosya nesneyi sahip olduğunuzda, okuma, yazma, oluşturmak için yalıtılmış depolama yöntemleri kullanabilir ve dosyaları ve dizinleri silin.  
  
 Kod gelen geçirme engeller hiçbir mekanizması bir <xref:System.IO.IsolatedStorage.IsolatedStorageFile> kodunu nesnesine deposu almak için yeterli erişimi yok. Etki alanı ve derleme kimlikleri ve yalıtılmış depolama izinleri işaretli yalnızca başvuru olduğunda bir <xref:System.IO.IsolatedStorage.IsolatedStorage> nesne elde edilir, genellikle içinde <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, veya <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> yöntemi. Başvurular koruma <xref:System.IO.IsolatedStorage.IsolatedStorageFile> nesnedir, bu nedenle, bu başvuruları kullanan kodu sorumluluğudur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, kullanıcı ve derlemeye göre yalıtılmış bir mağaza alma bir sınıfın basit bir örnek sağlar. Kullanıcı, etki alanı ve derleme tarafından ekleyerek yalıtılmış olduğundan bir depolama almak için kod değiştirilebilir <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Domain?displayProperty=nameWithType> bağımsız değişkenler için <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> yöntemi geçirir.  
  
 Kod çalıştırdıktan sonra bir depolama yazarak oluşturulduğunu doğrulayabilirsiniz **StoreAdm/List** komut satırında. Bu çalıştırır [yalıtılmış depolama aracı (Storeadm.exe)](../../../docs/framework/tools/storeadm-exe-isolated-storage-tool.md) ve tüm yalıtılmış geçerli kullanıcı için depolar listeler.  
  
 [!code-cpp[Conceptual.IsolatedStorage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#7)]
 [!code-csharp[Conceptual.IsolatedStorage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#7)]
 [!code-vb[Conceptual.IsolatedStorage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#7)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageScope>  
 [Yalıtılmış Depolama](../../../docs/standard/io/isolated-storage.md)  
 [Yalıtım Türleri](../../../docs/standard/io/types-of-isolation.md)  
 [Ortak Dil Çalışma Zamanı Modülündeki Bütünleştirilmiş Kodlar](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
