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
ms.openlocfilehash: dfebcc9acf0b699f898c106921d15ce0294bc5d2
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75707139"
---
# <a name="how-to-find-existing-files-and-directories-in-isolated-storage"></a>Nasıl yapılır: Yalıtılmış Depolamada Mevcut Dosya ve Dizinleri Bulma

Yalıtılmış depolamada bir dizin aramak için <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=nameWithType> yöntemini kullanın. Bu yöntem, bir arama modelini temsil eden bir dize alır. Arama düzeninde tek karakterlik (?) ve çok karakterli (\*) joker karakterler kullanabilirsiniz, ancak joker karakterler adın son bölümünde görünmelidir. Örneğin, `directory1/*ect*` geçerli bir arama dizesidir, ancak `*ect*/directory2` değildir.  
  
 Bir dosya aramak için <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=nameWithType> yöntemini kullanın. <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> için geçerli olan arama dizelerindeki joker karakterler için kısıtlama, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>için de geçerlidir.  
  
 Bu yöntemlerin hiçbiri özyinelemeli değildir; <xref:System.IO.IsolatedStorage.IsolatedStorageFile> sınıfı, Deponuzdaki tüm dizinleri veya dosyaları listelemek için herhangi bir yöntem sağlamaz. Ancak özyinelemeli yöntemler aşağıdaki kod örneğinde gösterilmiştir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, yalıtılmış bir depoda dosyaların ve dizinlerin nasıl oluşturulacağını göstermektedir. İlk olarak, Kullanıcı, etki alanı ve derleme için yalıtılmış bir mağaza alınır ve `isoStore` değişkenine yerleştirilir. <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A> yöntemi, birkaç farklı dizin ayarlamak için kullanılır ve <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29> Oluşturucu bu dizinlerde bazı dosyaları oluşturur. Kod daha sonra `GetAllDirectories` yönteminin sonuçları boyunca döngü yapılır. Bu yöntem, geçerli dizindeki tüm dizin adlarını bulmak için <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> kullanır. Bu adlar bir dizide depolanır ve sonra, bulduğu her bir dizine geçerek kendisini çağırır `GetAllDirectories`. Sonuç olarak, tüm dizin adları bir dizide döndürülür. Ardından, kod `GetAllFiles` yöntemini çağırır. Bu yöntem, tüm dizinlerin adlarını bulmak için `GetAllDirectories` çağırır ve sonra <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> yöntemini kullanarak her bir dizini dosyalar için denetler. Sonuç, görüntüleme için bir dizide döndürülür.  
  
 [!code-cpp[Conceptual.IsolatedStorage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source8.cpp#9)]
 [!code-csharp[Conceptual.IsolatedStorage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source8.cs#9)]
 [!code-vb[Conceptual.IsolatedStorage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source8.vb#9)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [Yalıtılmış Depolama](../../../docs/standard/io/isolated-storage.md)
