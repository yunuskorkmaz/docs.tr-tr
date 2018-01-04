---
title: "Nasıl yapılır: Tanımlayıcı Adlı Bir Derlemeye Başvurma"
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
- strong-named assemblies, compile-time references
- compile-time assembly referencing
- assemblies [.NET Framework], strong-named
- assembly binding, strong-named
ms.assetid: 4c6a406a-b5eb-44fa-b4ed-4e95bb95a813
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a5934f67387e29bfbd4f011ad2ba47f50d81b983
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-reference-a-strong-named-assembly"></a>Nasıl yapılır: Tanımlayıcı Adlı Bir Derlemeye Başvurma
Başvuran türleri veya kesin adlandırılmış bir derleme kaynaklarında işlemi genellikle saydamdır. Başvuru (erken bağlama) derleme zamanında ya da çalışma zamanında yapabilirsiniz.  
  
 Derleme zamanı referans derlemenizi açıkça başka bir derlemeye başvuran derleyiciye belirtmek oluşur. Derleme zamanı başvuran kullandığınızda, derleyici, otomatik olarak hedeflenen tanımlayıcı adlı derleme ortak anahtarını alır ve derlenmiş derlemenin derleme başvurusu yerleştirir.  
  
> [!NOTE]
>  Tanımlayıcı adlı bir derleme yalnızca diğer tanımlayıcı adlı derlemeler türlerinden kullanabilirsiniz. Aksi takdirde, tanımlayıcı adlı derleme güvenliğini tehlikeye.  
  
### <a name="to-make-a-compile-time-reference-to-a-strong-named-assembly"></a>Tanımlayıcı adlı bir derleme zamanı başvuru yapma  
  
1.  Komut satırında, aşağıdaki komutu yazın:  
  
     \<*derleyici komut*> **/reference:**\<*derleme adı*>  
  
     Bu komutta *derleyici komut* derleyici komut kullanıyorsanız, dil ve *derleme adı* başvurulan tanımlayıcı adlı derleme adıdır. Gibi diğer derleyici seçenekleri kullanabilir **/t:library** Kitaplık derlemesi oluşturma seçeneği.  
  
 Aşağıdaki örnek adlı bir derleme oluşturur `myAssembly.dll` adlı güçlü adlı bir derlemeye başvuruyor `myLibAssembly.dll` kod modülünden adlı `myAssembly.cs`.  
  
```  
csc /t:library myAssembly.cs /reference:myLibAssembly.dll  
```  
  
### <a name="to-make-a-run-time-reference-to-a-strong-named-assembly"></a>Tanımlayıcı adlı bir derleme çalışma zamanı başvuru yapma  
  
1.  Tanımlayıcı adlı bir derleme çalışma zamanı başvuru yaptığınızda (kullanarak örneğin, <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> veya <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> yöntemi), başvurulan derlemeyi tanımlayıcı adlı görünen adını kullanmanız gerekir. Bir görünen ad söz dizimi aşağıdaki gibidir:  
  
     \<*derleme adı*>**,** \< *sürüm numarası*>**,** \<  *kültür*>**,** \< *ortak anahtar belirteci*>  
  
     Örneğin:  
  
    ```  
    myDll, Version=1.1.0.0, Culture=en, PublicKeyToken=03689116d3a4ae33   
    ```  
  
     Bu örnekte, `PublicKeyToken` onaltılık ortak anahtar belirteci biçimidir. Kültür değer yoksa kullanmak `Culture=neutral`.  
  
 Aşağıdaki kod örneğinde bu bilgilerle kullanmayı gösterir <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemi.  
  
 [!code-cpp[Assembly.Load1#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Assembly.Load1/CPP/load2.cpp#3)]
 [!code-csharp[Assembly.Load1#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Assembly.Load1/CS/load2.cs#3)]
 [!code-vb[Assembly.Load1#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Assembly.Load1/VB/load2.vb#3)]  
  
 Aşağıdaki kullanarak belirli bir derleme için ortak anahtar ve ortak anahtar belirteci, onaltılık biçimde yazdırabilirsiniz [tanımlayıcı ad (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) komutu:  
  
 **sn - Tp \<**  *derleme***>**  
  
 Ortak bir anahtar dosyası varsa, bunun yerine aşağıdaki komutu kullanın (komut satırı seçeneğini kasasındaki fark unutmayın):  
  
 **sn - tp \<**  *derleme***>**  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kesin Adlandırılmış Bütünleştirilmiş Kodlar Oluşturma ve Kullanma](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
