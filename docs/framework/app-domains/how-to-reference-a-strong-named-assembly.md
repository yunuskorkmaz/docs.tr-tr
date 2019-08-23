---
title: 'Nasıl yapılır: Tanımlayıcı Adlı Bir Derlemeye Başvurma'
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 080d05a27b9e0b6ad4ff52d67ef8d9209dc1c697
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927950"
---
# <a name="how-to-reference-a-strong-named-assembly"></a>Nasıl yapılır: Tanımlayıcı Adlı Bir Derlemeye Başvurma
Tanımlayıcı adlı bir derlemede tür veya kaynaklara başvurma işlemi genellikle saydamdır. Başvuruyu derleme zamanında (erken bağlama) veya çalışma zamanında yapabilirsiniz.  
  
 Derleyiciye, derlemenizin açıkça başka bir derlemeye başvuruda bulunduğunu belirttiğinizde derleme zamanı başvurusu oluşur. Derleme zamanı başvurusu kullandığınızda, derleyici hedeflenen tanımlayıcı adlı derlemenin ortak anahtarını otomatik olarak alır ve derlenen derlemenin derleme başvurusuna koyar.  
  
> [!NOTE]
> Tanımlayıcı adlı bir derleme, yalnızca diğer tanımlayıcı adlı derlemelerden türleri kullanabilir. Aksi takdirde, tanımlayıcı adlı derlemenin güvenliği tehlikeye girebilir.  
  
### <a name="to-make-a-compile-time-reference-to-a-strong-named-assembly"></a>Tanımlayıcı adlı bir derlemeye derleme zamanı başvurusu yapmak için  
  
1. Komut satırında, aşağıdaki komutu yazın:  
  
     \<*Derleyici komutu*>  **/Reference:** \<*derleme adı*>  
  
     Bu komutta *derleyici komutu* , kullanmakta olduğunuz dilin derleyici komutu ve *derleme adı* , başvurulmakta olan tanımlayıcı adlı derlemenin adıdır. Ayrıca, bir kitaplık derlemesi oluşturmak için **/t: Library** seçeneği gibi diğer derleyici seçeneklerini de kullanabilirsiniz.  
  
 Aşağıdaki örnek, adlı bir kod modülünden `myAssembly.dll` `myAssembly.cs`çağrılan `myLibAssembly.dll` tanımlayıcı adlı bir derlemeye başvuran adlı bir derleme oluşturur.  
  
```  
csc /t:library myAssembly.cs /reference:myLibAssembly.dll  
```  
  
### <a name="to-make-a-run-time-reference-to-a-strong-named-assembly"></a>Tanımlayıcı adlı bir derlemeye çalışma zamanı başvurusu yapmak için  
  
1. Tanımlayıcı adlı bir derlemeye (örneğin, <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> veya <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> yöntemini kullanarak) çalışma zamanı başvurusu yaptığınızda, başvurulan tanımlayıcı adlı derlemenin görünen adını kullanmanız gerekir. Görünen adın sözdizimi aşağıdaki gibidir:  
  
     \<*bütünleştirilmiş kod adı*> **,** sürümnumarası> , kültür, ortak\<anahtar belirteci> \< \<>  
  
     Örneğin:  
  
    ```  
    myDll, Version=1.1.0.0, Culture=en, PublicKeyToken=03689116d3a4ae33   
    ```  
  
     Bu örnekte, `PublicKeyToken` ortak anahtar belirtecinin onaltılı biçimidir. Kültür değeri yoksa kullanın `Culture=neutral`.  
  
 Aşağıdaki kod örneği, bu bilgileri <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemiyle nasıl kullanacağınızı gösterir.  
  
 [!code-cpp[Assembly.Load1#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Assembly.Load1/CPP/load2.cpp#3)]
 [!code-csharp[Assembly.Load1#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Assembly.Load1/CS/load2.cs#3)]
 [!code-vb[Assembly.Load1#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Assembly.Load1/VB/load2.vb#3)]  
  
 Aşağıdaki [tanımlayıcı ad (sn. exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) komutunu kullanarak, belirli bir derleme için ortak anahtar ve ortak anahtar belirtecinin onaltılık biçimini yazdırabilirsiniz:  
  
 **sn-TP \<**  *derlemesi* **>**  
  
 Ortak anahtar dosyanız varsa, bunun yerine aşağıdaki komutu kullanabilirsiniz (komut satırı seçeneğinde büyük/küçük harf farkını aklınızda bulabilirsiniz):  
  
 **sn-TP \<**  *ortak anahtar dosyası* **>**  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kesin Adlandırılmış Bütünleştirilmiş Kodlar Oluşturma ve Kullanma](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
