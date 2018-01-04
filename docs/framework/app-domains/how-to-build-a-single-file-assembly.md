---
title: "Nasıl yapılır: Tek Dosyalı Derleme Oluşturma"
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
helpviewer_keywords:
- assembly manifest, single-file assemblies
- library assemblies
- command-line compilers
- assemblies [.NET Framework], single-file
- output file name for assemblies
- code modules
- single-file assemblies
ms.assetid: a6063221-43a5-4d3e-814c-288a4ec69aec
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bd9f2bab23fff1bbc4ebb521b167ac8031af3bc7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-build-a-single-file-assembly"></a>Nasıl yapılır: Tek Dosyalı Derleme Oluşturma
Tür bilgilerini ve uygulama, derleme basit türü olan tek dosyalı derleme içeren yanı sıra [derleme bildirimi](../../../docs/framework/app-domains/assembly-manifest.md). Komut satırı derleyicileri kullanabilirsiniz veya [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] tek dosyalı derleme oluşturmak için. Varsayılan olarak, derleyici .exe uzantısına bir derleme dosyası oluşturur.  
  
> [!NOTE]
>  [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)]C# ve Visual Basic için yalnızca tek dosya derlemeleri oluşturmak için kullanılabilir. Birden çok dosya derlemeleri oluşturmak istiyorsanız, komut satırı derleyicileri kullanmalısınız veya [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] Visual C++ için.  
  
 Aşağıdaki yordamları kullanarak komut satırı derleyicileri tek dosya derlemeleri oluşturmayı gösterir.  
  
### <a name="to-create-an-assembly-with-an-exe-extension"></a>Bir .exe uzantısına bir derleme oluşturmak için  
  
1.  Komut satırında, aşağıdaki komutu yazın:  
  
     \<*derleyici komut*> \<*modül adı*>  
  
     Bu komutta *derleyici komut* derleyici komut, kod modülünde kullanılan dil ve *modül adı* derlemeye derlemek için kod modülü adıdır.  
  
 Aşağıdaki örnek adlı bir derleme oluşturur `myCode.exe` kod modülünden adlı `myCode`.  
  
```csharp  
csc myCode.cs  
```  
  
```vb  
vbc myCode.vb  
```  
  
#### <a name="to-create-an-assembly-with-an-exe-extension-and-specify-the-output-file-name"></a>Bir .exe uzantılı bir derlemeyi oluşturun ve çıktı dosyası adını belirtmek için  
  
1.  Komut satırında, aşağıdaki komutu yazın:  
  
     \<*derleyici komut*> **/out:**\<*dosya adı*> \<*modül adı*>  
  
     Bu komutta *derleyici komut* , kod modülünde kullanılan dilin derleyici komut *dosya adı* çıktı dosyası adı ve *modül adı* adıdır derlemeye derlemek için kod modülü.  
  
 Aşağıdaki örnek adlı bir derleme oluşturur `myAssembly.exe` kod modülünden adlı `myCode`.  
  
```csharp  
csc /out:myAssembly.exe myCode.cs  
```  
  
```vb  
vbc /out:myAssembly.exe myCode.vb  
```  
  
## <a name="creating-library-assemblies"></a>Kitaplık derlemeleri oluşturma  
 Kitaplık derlemesi bir sınıf kitaplığı'na benzer. Diğer derlemelerden tarafından başvurulan türler içerir, ancak yürütme başlamak için hiçbir giriş noktası yok.  
  
#### <a name="to-create-a-library-assembly"></a>Kitaplık derlemesi oluşturmak için  
  
1.  Komut satırında, aşağıdaki komutu yazın:  
  
     \<*derleyici komut*> **/t:library** \< *modül adı*>  
  
     Bu komutta *derleyici komut* derleyici komut, kod modülünde kullanılan dil ve *modül adı* derlemeye derlemek için kod modülü adıdır. Gibi diğer derleyici seçenekleri kullanabilir **/out:** seçeneği.  
  
 Aşağıdaki örnek adlı bir kitaplık derlemesi oluşturur `myCodeAssembly.dll` kod modülünden adlı `myCode`.  
  
```csharp  
csc /out:myCodeLibrary.dll /t:library myCode.cs  
```  
  
```vb  
vbc /out:myCodeLibrary.dll /t:library myCode.vb  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bütünleştirilmiş Kodlar Oluşturma](../../../docs/framework/app-domains/create-assemblies.md)  
 [Çok Dosyalı Bütünleştirilmiş Kodlar](../../../docs/framework/app-domains/multifile-assemblies.md)  
 [Nasıl yapılır: Çok Dosyalı Bütünleştirilmiş Kod Derleme](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 [Bütünleştirilmiş Kodlarla Programlama](../../../docs/framework/app-domains/programming-with-assemblies.md)
