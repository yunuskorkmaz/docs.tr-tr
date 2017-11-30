---
title: "Nasıl yapılır: Yalıtılmış Depolamada Mevcut Dosya ve Dizinleri Bulma"
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
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 656c390358b6f6a671cf3ef11ea7be75f897d21c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
