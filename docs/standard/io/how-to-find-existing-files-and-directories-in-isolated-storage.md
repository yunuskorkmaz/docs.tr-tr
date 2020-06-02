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
ms.openlocfilehash: ec1d1fbdefdad3ec0dd2c07fbc1278e4d1d217c6
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291857"
---
# <a name="how-to-find-existing-files-and-directories-in-isolated-storage"></a>Nasıl yapılır: Yalıtılmış Depolamada Mevcut Dosya ve Dizinleri Bulma

Yalıtılmış depolamada bir dizin aramak için <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=nameWithType> yöntemini kullanın. Bu yöntem, bir arama modelini temsil eden bir dize alır. Arama düzeninde hem tek karakterli (?) hem çok karakterli ( \* ) joker karakterleri kullanabilirsiniz, ancak joker karakterlerin adın son bölümünde görünmesi gerekir. Örneğin, `directory1/*ect*` geçerli bir arama dizesidir, ancak `*ect*/directory2` değildir.  
  
 Bir dosya aramak için <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=nameWithType> yöntemini kullanın. İçin geçerli olan arama dizelerindeki joker karakterler için olan kısıtlama, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> için de geçerlidir <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> .  
  
 Bu yöntemlerin hiçbiri özyinelemeli değildir; <xref:System.IO.IsolatedStorage.IsolatedStorageFile>sınıfı, Deponuzdaki tüm dizinleri veya dosyaları listelemek için herhangi bir yöntem sağlamaz. Ancak özyinelemeli yöntemler aşağıdaki kod örneğinde gösterilmiştir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, yalıtılmış bir depoda dosyaların ve dizinlerin nasıl oluşturulacağını göstermektedir. İlk olarak, Kullanıcı, etki alanı ve derleme için yalıtılmış bir mağaza alınır ve `isoStore` değişkenine yerleştirilir. <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A>Yöntemi birkaç farklı dizin ayarlamak için kullanılır ve <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29> Oluşturucu bu dizinlerde bazı dosyalar oluşturur. Kod daha sonra yöntemin sonuçları boyunca döngü yapılır `GetAllDirectories` . Bu yöntem, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> geçerli dizindeki tüm dizin adlarını bulmak için kullanır. Bu adlar bir dizide depolanır ve sonra `GetAllDirectories` bulduğu her bir dizine geçerek kendisini çağırır. Sonuç olarak, tüm dizin adları bir dizide döndürülür. Ardından, kod `GetAllFiles` yöntemini çağırır. Bu yöntem, `GetAllDirectories` tüm dizinlerin adlarını bulmak için öğesini çağırır ve sonra yöntemini kullanarak her bir dizini dosyalar için denetler <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> . Sonuç, görüntüleme için bir dizide döndürülür.  
  
 [!code-cpp[Conceptual.IsolatedStorage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source8.cpp#9)]
 [!code-csharp[Conceptual.IsolatedStorage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source8.cs#9)]
 [!code-vb[Conceptual.IsolatedStorage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source8.vb#9)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [Yalıtılmış depolama](isolated-storage.md)
