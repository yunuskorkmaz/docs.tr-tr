---
title: 'Nasıl yapılır: Birden çok dosyalı derleme oluşturma'
description: Yordamın her adımını göstermek için örnek kod kullanarak .NET 'te çok dosyalı bir derleme derlemeyi (oluşturmayı) öğrenin.
ms.date: 08/20/2019
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
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 261c5583-8a76-412d-bda7-9b8ee3b131e5
ms.openlocfilehash: a4c298284950ba2989bb73e6d3383b3c4024e6e7
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104950"
---
# <a name="how-to-build-a-multifile-assembly"></a>Nasıl yapılır: Birden çok dosyalı derleme oluşturma

Bu makalede, çok dosyalı bir derlemenin nasıl oluşturulacağı ve yordamdaki her adımın gösterildiği kod nasıl kullanılacağı açıklanmaktadır.

> [!NOTE]
> C# ve Visual Basic için Visual Studio IDE yalnızca tek dosya derlemeler oluşturmak için kullanılabilir. Çoklu dosya derlemeleri oluşturmak istiyorsanız, Visual C++ komut satırı derleyicilerini veya Visual Studio 'Yu kullanmanız gerekir. Çok dosyalı derlemeler yalnızca .NET Framework tarafından desteklenir.

## <a name="create-a-multifile-assembly"></a>Çoklu dosya derlemesi oluşturma

1. Derlemedeki diğer modüller tarafından kod modüllerine başvuruda bulunulan ad alanlarını içeren tüm dosyaları derleyin. Kod modülleri için varsayılan uzantı *. netmodule*'dir.

   Örneğin, dosyada adlı bir `Stringer` sınıf içeren bir ad alanı olduğunu varsayalım `myStringer` `Stringer` . `Stringer`Sınıfı, `StringerMethod` konsola tek bir satır yazan adlı bir yöntemi içerir.

   ```cpp
   // Assembly building example in the .NET Framework.
   using namespace System;

   namespace myStringer
   {
       public ref class Stringer
       {
       public:
           void StringerMethod()
           {
               System::Console::WriteLine("This is a line from StringerMethod.");
           }
       };
   }
   ```

   ```csharp
   // Assembly building example in the .NET Framework.
   using System;

   namespace myStringer
   {
       public class Stringer
       {
           public void StringerMethod()
           {
               System.Console.WriteLine("This is a line from StringerMethod.");
           }
       }
   }
   ```

   ```vb
   ' Assembly building example in the .NET Framework.
   Namespace myStringer
       Public Class Stringer
           Public Sub StringerMethod()
               System.Console.WriteLine("This is a line from StringerMethod.")
           End Sub
       End Class
   End Namespace
   ```

2. Bu kodu derlemek için aşağıdaki komutu kullanın:

   ```cpp
   cl /clr:pure /LN Stringer.cpp
   ```

   ```csharp
   csc /t:module Stringer.cs
   ```

   ```vb
   vbc /t:module Stringer.vb
   ```

   **/T:** derleyici seçeneğiyle *Modül* parametresini belirtme, dosyanın derleme yerine bir modül olarak derlenmesi gerektiğini gösterir. Derleyici, bir derlemeye eklenebilecek *strger. netmodule*adlı bir modül oluşturur.

3. Kodda başvurulan diğer modülleri göstermek için gerekli derleyici seçeneklerini kullanarak diğer tüm modülleri derleyin. Bu adım, **/addmodule** derleyici seçeneğini kullanır.

   Aşağıdaki örnekte, *istemci* adlı bir kod modülünün, `Main` 1. adımda oluşturulan *Stringer.dll* modülündeki bir yönteme başvuran bir giriş noktası yöntemi vardır.

   ```cpp
   #using "Stringer.netmodule"

   using namespace System;
   using namespace myStringer; //The namespace created in Stringer.netmodule.

   ref class MainClientApp
   {
       // Static method Main is the entry point method.
   public:
       static void Main()
       {
           Stringer^ myStringInstance = gcnew Stringer();
           Console::WriteLine("Client code executes");
           myStringInstance->StringerMethod();
       }
   };

   int main()
   {
       MainClientApp::Main();
   }
   ```

   ```csharp
   using System;
   using myStringer;

   class MainClientApp
   {
       // Static method Main is the entry point method.
       public static void Main()
       {
           Stringer myStringInstance = new Stringer();
           Console.WriteLine("Client code executes");
           myStringInstance.StringerMethod();
       }
   }
   ```

   ```vb
   Imports myStringer

   Class MainClientApp
       ' Static method Main is the entry point method.
       Public Shared Sub Main()
           Dim myStringInstance As New Stringer()
           Console.WriteLine("Client code executes")
           myStringInstance.StringerMethod()
       End Sub
   End Class
   ```

4. Bu kodu derlemek için aşağıdaki komutu kullanın:

   ```cpp
   cl /clr:pure /FUStringer.netmodule /LN Client.cpp
   ```

   ```csharp
   csc /addmodule:Stringer.netmodule /t:module Client.cs
   ```

   ```vb
   vbc /addmodule:Stringer.netmodule /t:module Client.vb
   ```

   Bu modül gelecekteki bir adımda bir derlemeye eklenecağından **/t: Module** seçeneğini belirtin. *İstemci* içindeki kod, *strger. netmodule*içindeki kodla oluşturulan bir ad alanına başvurduğundan **/addmodule** seçeneğini belirtin. Derleyici, farklı bir modül olan *strger. netmodule*'e yönelik bir başvuru içeren *Client. netmodule* adlı bir modül üretir.

   > [!NOTE]
   > C# ve Visual Basic derleyicileri, aşağıdaki iki farklı sözdizimleri kullanılarak çok dosyalı derlemeler doğrudan oluşturulmasını destekler.
   >
   > İki derleme iki dosya derleme oluşturur:
   >
   >   ```cpp
   >   cl /clr:pure /LN Stringer.cpp
   >   cl /clr:pure Client.cpp /link /ASSEMBLYMODULE:Stringer.netmodule
   >   ```
   >
   >   ```csharp
   >   csc /t:module Stringer.cs
   >   csc Client.cs /addmodule:Stringer.netmodule
   >   ```
   >
   >   ```vb
   >   vbc /t:module Stringer.vb
   >   vbc Client.vb /addmodule:Stringer.netmodule
   >   ```
   >
   > Bir derleme iki dosya derleme oluşturur:
   >
   >   ```cpp
   >   cl /clr:pure /LN Stringer.cpp
   >   cl /clr:pure Client.cpp /link /ASSEMBLYMODULE:Stringer.netmodule
   >   ```
   >
   >   ```csharp
   >   csc /out:Client.exe Client.cs /out:Stringer.netmodule Stringer.cs
   >   ```
   >
   >   ```vb
   >   vbc /out:Client.exe Client.vb /out:Stringer.netmodule Stringer.vb
   >   ```

5. Derleme bildirimini içeren çıktı dosyasını oluşturmak için [derleme Bağlayıcısı 'nı (Al.exe)](../tools/al-exe-assembly-linker.md) kullanın. Bu dosya, derlemenin parçası olan tüm modüller veya kaynaklar için başvuru bilgileri içerir.

    Komut isteminde aşağıdaki komutu yazın:

    **Al** \<*module name*> \<*module name*>... **/Main:** \<*method name*> **/Out:** \<*file name*> **/target:**\<*assembly file type*>

    Bu komutta, *Modül adı* bağımsız değişkenleri derlemeye dahil edilecek her modülün adını belirtir. **/Main:** seçeneği derlemenin giriş noktası olan yöntem adını belirtir. **/Out:** seçeneği, derleme meta verilerini içeren çıkış dosyasının adını belirtir. **/Target:** seçeneği, derlemenin bir konsol uygulaması yürütülebilir (*. exe*) dosyası, bir Windows yürütülebilir (*. Win*) dosyası veya bir kitaplık (*. lib*) dosyası olduğunu belirtir.

    Aşağıdaki örnekte, *Al.exe* *myAssembly.exe*adlı konsol uygulaması yürütülebilir dosyası olan bir derleme oluşturur. Uygulama, *istemci. netmodule* ve *strger. netmodule*adlı iki modülden ve yalnızca derleme meta verilerini içeren *myAssembly.exe*adlı yürütülebilir dosya ile oluşur. Derlemenin giriş noktası, `Main` sınıfındaki, `MainClientApp` *Client.dll*bulunan yöntemdir.

    ```cmd
    al Client.netmodule Stringer.netmodule /main:MainClientApp.Main /out:myAssembly.exe /target:exe
    ```

    Bir derlemenin içeriğini incelemek veya bir dosyanın derleme ya da modülle olduğunu anlamak için [MSIL Disassembler (Ildasm.exe)](../tools/ildasm-exe-il-disassembler.md) kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Derleme oluşturma](../../standard/assembly/create.md)
- [Nasıl yapılır: derleme içeriğini görüntüleme](../../standard/assembly/view-contents.md)
- [Çalışma zamanının derlemeleri nasıl konumlandırır](../deployment/how-the-runtime-locates-assemblies.md)
- [Birden çok dosyalı derlemeler](multifile-assemblies.md)
