---
title: "Nasıl yapılır: Birden Fazla Dosya Derleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- entry point for assembly
- compiling assemblies
- Al.exe
- command-line compilers
- assembly manifest, multifile assemblies
- assemblies [.NET Framework], compiling
- Assembly Linker
- code modules
- multifile assemblies
ms.assetid: 261c5583-8a76-412d-bda7-9b8ee3b131e5
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f77922d08ce17f8b8659eac0dba5a46ca33a7502
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-build-a-multifile-assembly"></a>Nasıl yapılır: Birden Fazla Dosya Derleme
Bu makalede, birden fazla dosya derlemesi oluşturma açıklanmaktadır ve yordamda her adım gösterilmektedir kodu sağlar.  
  
> [!NOTE]
>  C# ve Visual Basic için Visual Studio IDE yalnızca tek dosya derlemeleri oluşturmak için kullanılabilir. Birden çok dosya derlemeleri oluşturmak istiyorsanız, Visual C++ ile komut satırı derleyicileri veya Visual Studio kullanmanız gerekir.  
  
### <a name="to-create-a-multifile-assembly"></a>Birden fazla dosya derlemesi oluşturmak için  
  
1.  Bütünleştirilmiş kod modüllere diğer modüller tarafından başvurulan ad alanları içeren tüm dosyalar derleyin. Kod modülleri için varsayılan .netmodule uzantısıdır.  
  
     Örneğin, diyelim `Stringer` dosya adlı bir ad alanına sahip `myStringer`, adlı bir sınıf içerir `Stringer`. `Stringer` Sınıfı içeren adlı bir yöntem `StringerMethod` , tek bir satır konsola yazar.  
  
     [!code-cpp[Conceptual.Assembly.Multifile#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/stringer.cpp#1)]
     [!code-csharp[Conceptual.Assembly.Multifile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/stringer.cs#1)]
     [!code-vb[Conceptual.Assembly.Multifile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/stringer.vb#1)]  
  
     Bu kodu derlemek için aşağıdaki komutu kullanın:  
  
     [!code-cpp[Conceptual.Assembly.Multifile#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/stringer.cpp#2)]
     [!code-csharp[Conceptual.Assembly.Multifile#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/stringer.cs#2)]
     [!code-vb[Conceptual.Assembly.Multifile#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/stringer.vb#2)]  
  
     Belirtme *Modülü* parametresiyle **/t:** derleyici seçeneği, dosyanın bir modül olarak yerine bir derlemeyi olarak derlenmesi gerektiğini gösterir. Adlı bir modül derleyici üreten `Stringer.netmodule`, hangi eklenebilir bir derlemeye.  
  
2.  Kod içinde başvurulan diğer modüller göstermek için gerekli derleyici seçenekleri kullanarak tüm diğer modüllerin derleyin. Bu adımı kullanan **/addmodule** derleyici seçeneği.  
  
     Aşağıdaki örnekte, bir kod modülüne adlı `Client` bir giriş noktası sahip `Main` bir yönteme başvuran yöntemi `Stringer.dll` 1. adımda oluşturduğunuz modül.  
  
     [!code-cpp[Conceptual.Assembly.Multifile#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#3)]
     [!code-csharp[Conceptual.Assembly.Multifile#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#3)]
     [!code-vb[Conceptual.Assembly.Multifile#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#3)]  
  
     Bu kodu derlemek için aşağıdaki komutu kullanın:  
  
     [!code-cpp[Conceptual.Assembly.Multifile#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#4)]
     [!code-csharp[Conceptual.Assembly.Multifile#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#4)]
     [!code-vb[Conceptual.Assembly.Multifile#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#4)]  
  
     Belirtin **/t:module** Bu modülün derleme için bir sonraki adımda eklenen olacağından. Belirtin **/addmodule** olacağından kodda `Client` kod tarafından oluşturulan bir ad alanı referanslarını `Stringer.netmodule`. Adlı bir modül derleyici üreten `Client.netmodule` başka bir modül için bir başvuru içeren `Stringer.netmodule`.  
  
    > [!NOTE]
    >  C# ve Visual Basic derleyicileri doğrudan aşağıdaki iki farklı sözdizimi kullanarak birden çok dosya derlemeleri oluşturmayı destekler.  
    >   
    >  -   İki derlemeleri iki dosyalı derleme oluşturma:  
    >   
    >      [!code-cpp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#5)]
      [!code-csharp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#5)]
      [!code-vb[Conceptual.Assembly.Multifile#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#5)]  
    > -   Bir derleme iki dosyalı derleme oluşturur:  
    >   
    >      [!code-cpp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#6)]
      [!code-csharp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#6)]
      [!code-vb[Conceptual.Assembly.Multifile#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#6)]  
  
3.  Kullanım [derleme bağlayıcı (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) derleme bildirimi içerir çıktı dosyasını oluşturmak için. Bu dosya, tüm modülleri veya derlemenin parçası olan kaynaklar için başvuru bilgileri içerir.  
  
     Komut satırında, aşağıdaki komutu yazın:  
  
     **Al** \< *modül adı*> \<*modül adı*>... **/ main:**\<*yöntem adı*> **/out:**\<*dosya adı*> **/ Hedef:**\<*derleme dosya türü*>  
  
     Bu komutta *modül adı* bağımsız değişkenleri derlemeyi dahil etmek için her modül adı belirtin. **/Ana:** seçeneği derlemenin giriş noktası yöntem adını belirtir. **/Out:** seçeneği derleme meta verilerini içeren çıktı dosyası adını belirtir. **/Target:** seçeneği derleme bir konsol uygulama yürütülebilir dosyanın (.exe) dosyası, bir Windows yürütülebilir dosya (.win) dosyası ya da kitaplık (.lib) dosyası olduğunu belirtir.  
  
     Aşağıdaki örnekte, Al.exe adlı bir konsol uygulaması yürütülebilir bir derleme oluşturur `myAssembly.exe`. Uygulama adında iki modülden oluşur `Client.netmodule` ve `Stringer.netmodule`, yürütülebilir dosya adı verilen ve `myAssembly.exe,` yalnızca derleme meta verilerini içeriyor. Giriş noktası derlemenin `Main` sınıfında yöntemi `MainClientApp`, bulunan `Client.dll`.  
  
    ```  
    al Client.netmodule Stringer.netmodule /main:MainClientApp.Main /out:myAssembly.exe /target:exe   
    ```  
  
     Kullanabileceğiniz [MSIL ayrıştırıcı (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) bütünleştirilmiş içeriğini incelemek veya bir dosyanın bir derlemeyi ya da bir modül olup olmadığını belirlemek için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bütünleştirilmiş Kodlar Oluşturma](../../../docs/framework/app-domains/create-assemblies.md)  
 [Nasıl yapılır: Bütünleştirilmiş Kod İçeriklerini Görüntüleme](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)  
 [Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [Çok Dosyalı Bütünleştirilmiş Kodlar](../../../docs/framework/app-domains/multifile-assemblies.md)
