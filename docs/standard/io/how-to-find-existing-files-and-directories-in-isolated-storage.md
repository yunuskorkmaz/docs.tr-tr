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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75707139"
---
# <a name="how-to-find-existing-files-and-directories-in-isolated-storage"></a>Nasıl yapılır: Yalıtılmış Depolamada Mevcut Dosya ve Dizinleri Bulma

Yalıtılmış depolamada bir dizin <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=nameWithType> aramak için yöntemi kullanın. Bu yöntem, bir arama deseni temsil eden bir dize alır. Arama deseninde hem tek karakterli (?) hem de çok karakterli (\*) joker karakter kullanabilirsiniz, ancak joker karakterin adın son bölümünde görünmesi gerekir. Örneğin, `directory1/*ect*` geçerli bir arama dizesi, ancak `*ect*/directory2` değildir.  
  
 Bir dosyayı aramak için <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=nameWithType> yöntemi kullanın. Arama dizeleri için geçerli olan joker karakter <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> kısıtlaması <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>da geçerlidir.  
  
 Bu yöntemlerin hiçbiri özyinelemeli değildir; <xref:System.IO.IsolatedStorage.IsolatedStorageFile> sınıf, mağazanızdaki tüm dizinleri veya dosyaları listelemek için herhangi bir yöntem sağlamaz. Ancak, özyinelemeli yöntemler aşağıdaki kod örneğinde gösterilmiştir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, yalıtılmış bir depoda dosyaların ve dizinlerin nasıl oluşturulup oluşturulabildiğini göstermektedir. İlk olarak, kullanıcı, etki alanı ve derleme için yalıtılmış `isoStore` bir mağaza alınır ve değişkene yerleştirilir. Yöntem <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A> birkaç farklı dizinler ayarlamak için kullanılır <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29> ve oluşturucu bu dizinlerde bazı dosyalar oluşturur. Kod daha sonra `GetAllDirectories` yöntemin sonuçları arasında döngüler. Bu yöntem, geçerli dizindeki tüm dizin adlarını bulmak için kullanır. <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> Bu adlar bir dizide depolanır ve bulduğu `GetAllDirectories` her dizide geçerek kendisini çağırır. Sonuç olarak, tüm dizin adları bir dizi döndürülür. Sonra, kod `GetAllFiles` yöntemi çağırır. Bu yöntem, tüm dizinlerin adlarını bulmak için çağırır `GetAllDirectories` ve sonra <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> yöntemi kullanarak dosyaları için her dizin denetler. Sonuç görüntülenmek için bir dizi döndürülür.  
  
 [!code-cpp[Conceptual.IsolatedStorage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source8.cpp#9)]
 [!code-csharp[Conceptual.IsolatedStorage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source8.cs#9)]
 [!code-vb[Conceptual.IsolatedStorage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source8.vb#9)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [Yalıtılmış Depolama](../../../docs/standard/io/isolated-storage.md)
