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
ms.openlocfilehash: 866be7970c43051dd7e2bf8d45ae779aca130a45
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-find-existing-files-and-directories-in-isolated-storage"></a>Nasıl yapılır: Yalıtılmış Depolamada Mevcut Dosya ve Dizinleri Bulma
Yalıtılmış Depolama dizinde aramak için kullanın <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=nameWithType> yöntemi. Bu yöntem, bir arama deseniyle temsil eden bir dize alır. Tek karakter (?) ve çok karakter (*) kullanabilirsiniz joker karakter arama deseni, ancak joker karakterler adının son bölümü görünmesi gerekir. Örneğin, `directory1/*ect*` geçerli bir arama dizesi ancak `*ect*/directory2` değil.  
  
 Bir dosyayı aramak için kullanın <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=nameWithType> yöntemi. Uygulandığı öğe arama dizelerini joker karakterleri için kısıtlama <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> için de geçerlidir <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>.  
  
 Bu yöntemlerin hiçbiri yinelemeli; <xref:System.IO.IsolatedStorage.IsolatedStorageFile> sınıfı, tüm dizinler veya deponuza dosyaları listeleme için herhangi bir yöntem sağlamanız değil. Ancak, yinelemeli yöntemler aşağıdaki kod örneğinde gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde dosyaları ve dizinleri yalıtılmış bir depolama alanına nasıl oluşturulacağını gösterir. İlk olarak, kullanıcı, etki alanı ve derleme için yalıtılmış bir deposu alınır ve bulundukları `isoStore` değişkeni. <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A> Yöntemi birkaç farklı dizinler, ayarlamak için kullanılır ve <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29> Oluşturucusu bu dizinleri bazı dosyaları oluşturur. Kod ardından sonuçları döngü `GetAllDirectories` yöntemi. Bu yöntem <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> geçerli dizindeki tüm dizin adlarını bulmak için. Bu adları bir dizide depolanır ve ardından `GetAllDirectories` kendisini bulduğu her dizin için geçirme çağırır. Sonuç olarak, tüm dizin adlarını dizi olarak döndürülür. Ardından, kod çağırır `GetAllFiles` yöntemi. Bu yöntemi çağırır `GetAllDirectories` tüm adlarını bulmak için dizinleri ve ardından onu denetler dosyaları için her bir dizin kullanarak <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> yöntemi. Görüntü için bir dizi sonuç döndürülür.  
  
 [!code-cpp[Conceptual.IsolatedStorage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source8.cpp#9)]
 [!code-csharp[Conceptual.IsolatedStorage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source8.cs#9)]
 [!code-vb[Conceptual.IsolatedStorage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source8.vb#9)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 [Yalıtılmış Depolama](../../../docs/standard/io/isolated-storage.md)
