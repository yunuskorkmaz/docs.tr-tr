---
title: 'Nasıl yapılır: Birden Fazla Dosya Derlemesi Oluşturma'
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a964e73cc41cebad33a3edc34b89ef240fbc62c8
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040850"
---
# <a name="how-to-build-a-multifile-assembly"></a>Nasıl yapılır: Birden Fazla Dosya Derlemesi Oluşturma

Bu makalede, çok dosyalı bir derlemenin nasıl oluşturulacağı ve yordamdaki her adımın gösterildiği kod nasıl kullanılacağı açıklanmaktadır.

> [!NOTE]
> Ve Visual Basic için C# VISUAL Studio IDE yalnızca tek dosya derlemeler oluşturmak için kullanılabilir. Çok dosyalı derlemeler oluşturmak istiyorsanız, komut satırı derleyicilerini veya Visual Studio 'Yu Visual C++Studio kullanmanız gerekir.

### <a name="to-create-a-multifile-assembly"></a>Çoklu dosya derlemesi oluşturmak için

01. Derlemedeki diğer modüller tarafından kod modüllerine başvuruda bulunulan ad alanlarını içeren tüm dosyaları derleyin. Kod modülleri için varsayılan uzantı. netmodule 'dir.

    Örneğin, `Stringer` dosyada adlı bir sınıf `Stringer`içeren bir `myStringer`ad alanı olduğunu varsayalım. Sınıfı, konsola tek bir satır `StringerMethod` yazan adlı bir yöntemi içerir. `Stringer`

    [!code-cpp[Conceptual.Assembly.Multifile#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/stringer.cpp#1)]
    [!code-csharp[Conceptual.Assembly.Multifile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/stringer.cs#1)]
    [!code-vb[Conceptual.Assembly.Multifile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/stringer.vb#1)]

    Bu kodu derlemek için aşağıdaki komutu kullanın:

    [!code-cpp[Conceptual.Assembly.Multifile#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/stringer.cpp#2)]
    [!code-csharp[Conceptual.Assembly.Multifile#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/stringer.cs#2)]
    [!code-vb[Conceptual.Assembly.Multifile#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/stringer.vb#2)]

    **/T:** derleyici seçeneğiyle *Modül* parametresini belirtme, dosyanın derleme yerine bir modül olarak derlenmesi gerektiğini gösterir. Derleyici, bir derlemeye eklenebilen adlı `Stringer.netmodule`bir modül üretir.

02. Kodda başvurulan diğer modülleri göstermek için gerekli derleyici seçeneklerini kullanarak diğer tüm modülleri derleyin. Bu adım, **/addmodule** derleyici seçeneğini kullanır.

    Aşağıdaki örnekte, adlı `Client` bir kod modülünün, 1. adımda oluşturulan `Stringer.dll` modüldeki `Main` bir yönteme başvuran bir giriş noktası yöntemi vardır.

    [!code-cpp[Conceptual.Assembly.Multifile#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#3)]
    [!code-csharp[Conceptual.Assembly.Multifile#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#3)]
    [!code-vb[Conceptual.Assembly.Multifile#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#3)]

    Bu kodu derlemek için aşağıdaki komutu kullanın:

    [!code-cpp[Conceptual.Assembly.Multifile#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#4)]
    [!code-csharp[Conceptual.Assembly.Multifile#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#4)]
    [!code-vb[Conceptual.Assembly.Multifile#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#4)]

    Bu modül gelecekteki bir adımda bir derlemeye eklenecağından **/t: Module** seçeneğini belirtin. İçindeki`Client` kod, içindeki `Stringer.netmodule`kod tarafından oluşturulan bir ad alanına başvurduğundan **/addmodule** seçeneğini belirtin. Derleyici, `Client.netmodule` `Stringer.netmodule`başka bir modüle başvuru içeren adlı bir modül üretir.

    >[!NOTE]
    >C# Ve Visual Basic derleyicileri, aşağıdaki iki farklı sözdizimleri kullanılarak çok dosyalı derlemeler doğrudan oluşturulmasını destekler.
    >
    >- İki derleme iki dosya derleme oluşturur:[!code-cpp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#5)]
    >  [!code-csharp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#5)]
    >  [!code-vb[Conceptual.Assembly.Multifile#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#5)]
    >
    >- Bir derleme iki dosya derleme oluşturur:[!code-cpp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#6)]
    >  [!code-csharp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#6)]
    >  [!code-vb[Conceptual.Assembly.Multifile#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#6)]

03. Derleme bildirimini içeren çıktı dosyasını oluşturmak için [derleme Bağlayıcısı (al. exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) kullanın. Bu dosya, derlemenin parçası olan tüm modüller veya kaynaklar için başvuru bilgileri içerir.

    Komut satırında, aşağıdaki komutu yazın:

    **Al** \< *Modül*adımodül> adı>...\< **/Main:** \<*Yöntem adı*>  **/Out:** dosyaadı\< **/target:** *Assembly dosya* türü\<> >

    Bu komutta, *Modül adı* bağımsız değişkenleri derlemeye dahil edilecek her modülün adını belirtir. **/Main:** seçeneği derlemenin giriş noktası olan yöntem adını belirtir. **/Out:** seçeneği, derleme meta verilerini içeren çıkış dosyasının adını belirtir. **/Target:** seçeneği, derlemenin bir konsol uygulaması yürütülebilir (. exe) dosyası, bir Windows yürütülebilir (. Win) dosyası veya bir kitaplık (. lib) dosyası olduğunu belirtir.

    Aşağıdaki örnekte, al. exe adlı `myAssembly.exe`bir konsol uygulaması yürütülebilir dosyası olan bir derleme oluşturur. Uygulama ve `Client.netmodule` `Stringer.netmodule`adlı iki modülden oluşur ve yalnızca derleme meta verilerini içeren yürütülebilir `myAssembly.exe,` dosya çağırılır. Derlemenin `Main` giriş noktası, sınıfındaki `MainClientApp` `Client.dll`' de bulunan yöntemidir.

    ```
    al Client.netmodule Stringer.netmodule /main:MainClientApp.Main /out:myAssembly.exe /target:exe
    ```

    Bir derlemenin içeriğini incelemek veya bir dosyanın derleme veya modülle olduğunu anlamak için [MSIL Disassembler (ıldadsm. exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Bütünleştirilmiş Kodlar Oluşturma](../../../docs/framework/app-domains/create-assemblies.md)
- [Nasıl yapılır: Derleme Içeriğini görüntüle](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)
- [Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [Çok Dosyalı Bütünleştirilmiş Kodlar](../../../docs/framework/app-domains/multifile-assemblies.md)
