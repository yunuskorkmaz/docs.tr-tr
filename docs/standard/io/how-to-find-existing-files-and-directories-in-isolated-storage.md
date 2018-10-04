---
title: 'Nasıl yapılır: Yalıtılmış Depolamada Mevcut Dosya ve Dizinleri Bulma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- stores, finding files and directories
- locating files in isolated storage file
- directories [.NET Framework], isolated storage
- isolated storage, finding files and directories
- data storage using isolated storage, finding files and directories
- files [.NET Framework], isolated storage
- data stores, finding files and directories
- locating directories in isolated storage file
- storing data using isolated storage, finding files and directories
ms.assetid: eb28458a-6161-4e7a-9ada-30ef93761b5c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 09c112374458b70a464291e898e9a880c8679773
ms.sourcegitcommit: 700b9003ea6bdd83a53458bbc436c9b5778344f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2018
ms.locfileid: "48261113"
---
# <a name="how-to-find-existing-files-and-directories-in-isolated-storage"></a>Nasıl yapılır: Yalıtılmış Depolamada Mevcut Dosya ve Dizinleri Bulma
Yalıtılmış Depolama bir dizinde aramak için kullanın <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=nameWithType> yöntemi. Bu yöntem bir arama deseni temsil eden bir dize alır. Hem tek karakterli (?) hem de birden çok karakter (*) kullanabilirsiniz joker karakterlere arama deseninde, ancak joker karakterler adının son bölümünde yer almalıdır. Örneğin, `directory1/*ect*` bir geçerli bir arama dizesi ancak `*ect*/directory2` değil.  
  
 Bir dosyayı aramak için kullanın <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=nameWithType> yöntemi. Geçerli arama dizelerini joker karakterleri için kısıtlama <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> için de geçerlidir <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>.  
  
 Bu yöntemlerin hiçbiri; özyinelemelidir <xref:System.IO.IsolatedStorage.IsolatedStorageFile> sınıfı, tüm dizinleri ve dosyaları mağazanızdaki listeleme herhangi bir yöntem sağlamaz. Ancak, yinelemeli yöntemleri aşağıdaki kod örneğinde gösterilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği bir yalıtılmış depoda dosyalar ve dizinler oluşturma işlemini göstermektedir. İlk olarak, kullanıcı, etki alanı ve derlemeye için yalıtılmış bir deposu alınır ve bulundukları `isoStore` değişkeni. <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A> Yöntemi birkaç farklı dizinler, ayarlamak için kullanılır ve <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29> Oluşturucu bazı dosyalar bu dizinlerde oluşturur. Kodu daha sonra sonuçları döngü `GetAllDirectories` yöntemi. Bu yöntemde <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> tüm dizin adları geçerli dizinde bulunamadı. Bu adlar bir dizi içinde depolanır ve ardından `GetAllDirectories` , bulduğu her dizinde geçirme kendisini çağırır. Sonuç olarak, tüm dizin adları bir dizi halinde döndürülür. Ardından, kodu çağıran `GetAllFiles` yöntemi. Bu yöntemin çağırdığı `GetAllDirectories` tüm adlarını bulmak için dizinleri ardından bunu denetler ve dosyaları için her bir dizin kullanarak <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> yöntemi. Sonucu görüntülemek için bir dizi döndürülür.  
  
 [!code-cpp[Conceptual.IsolatedStorage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source8.cpp#9)]
 [!code-csharp[Conceptual.IsolatedStorage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source8.cs#9)]
 [!code-vb[Conceptual.IsolatedStorage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source8.vb#9)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
- [Yalıtılmış Depolama](../../../docs/standard/io/isolated-storage.md)
