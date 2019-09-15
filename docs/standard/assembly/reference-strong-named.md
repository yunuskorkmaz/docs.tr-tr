---
title: 'Nasıl yapılır: Tanımlayıcı adlı bir derlemeye başvuru'
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies, compile-time references
- compile-time assembly referencing
- assemblies [.NET Framework], strong-named
- assembly binding, strong-named
ms.assetid: 4c6a406a-b5eb-44fa-b4ed-4e95bb95a813
author: rpetrusha
ms.author: ronpet
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 324cd42a2781202f19e7e1cb5055d571f0c58cf5
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973133"
---
# <a name="how-to-reference-a-strong-named-assembly"></a>Nasıl yapılır: Tanımlayıcı adlı bir derlemeye başvuru
Tanımlayıcı adlı bir derlemede tür veya kaynaklara başvurma işlemi genellikle saydamdır. Başvuruyu derleme zamanında (erken bağlama) veya çalışma zamanında yapabilirsiniz.  
  
Derleyiciye derlenen derlemenin başka bir derlemeye açıkça başvuruda bulunduğunu belirttiğinizde derleme zamanı başvurusu oluşur. Derleme zamanı başvurusu kullandığınızda, derleyici hedeflenen tanımlayıcı adlı derlemenin ortak anahtarını otomatik olarak alır ve derlenen derlemenin derleme başvurusuna koyar.
  
> [!NOTE]
> Tanımlayıcı adlı bir derleme, yalnızca diğer tanımlayıcı adlı derlemelerden türleri kullanabilir. Aksi takdirde, tanımlayıcı adlı derlemenin güvenliği tehlikeye girebilir.  
  
## <a name="make-a-compile-time-reference-to-a-strong-named-assembly"></a>Tanımlayıcı adlı bir derlemeye derleme zamanı başvurusu yapma  

Bir komut isteminde aşağıdaki komutu yazın:  

\<*Derleyici komutu*>  **/Reference:** \<*derleme adı*>  

Bu komutta *derleyici komutu* , kullanmakta olduğunuz dilin derleyici komutu ve *derleme adı* , başvurulmakta olan tanımlayıcı adlı derlemenin adıdır. Ayrıca, bir kitaplık derlemesi oluşturmak için **/t: Library** seçeneği gibi diğer derleyici seçeneklerini de kullanabilirsiniz.  

Aşağıdaki örnek, *MyAssembly.cs*adlı bir kod modülünden *myLibAssembly. dll* adlı güçlü adlı bir derlemeye başvuran *MyAssembly. dll* adlı bir derleme oluşturur.  

```cmd
csc /t:library myAssembly.cs /reference:myLibAssembly.dll  
```  

## <a name="make-a-run-time-reference-to-a-strong-named-assembly"></a>Tanımlayıcı adlı bir derlemeye çalışma zamanı başvurusu yapma  
  
Tanımlayıcı adlı bir derlemeye çalışma zamanı başvurusu yaptığınızda (örneğin, <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> veya <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> yöntemini kullanarak), başvurulan tanımlayıcı adlı derlemenin görünen adını kullanmanız gerekir. Görünen adın sözdizimi aşağıdaki gibidir:  

\<*bütünleştirilmiş kod adı*> **,** sürümnumarası> , kültür, ortak\<anahtar belirteci> \< \<>  

Örneğin:  

```console
myDll, Version=1.1.0.0, Culture=en, PublicKeyToken=03689116d3a4ae33   
```  

Bu örnekte, `PublicKeyToken` ortak anahtar belirtecinin onaltılı biçimidir. Kültür değeri yoksa kullanın `Culture=neutral`.  

Aşağıdaki kod örneği, bu bilgileri <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemiyle nasıl kullanacağınızı gösterir.  

```cpp
Assembly^ myDll =
    Assembly::Load("myDll, Version=1.0.0.1, Culture=neutral, PublicKeyToken=9b35aa32c18d4fb1");
```

```csharp
Assembly myDll =
    Assembly.Load("myDll, Version=1.0.0.1, Culture=neutral, PublicKeyToken=9b35aa32c18d4fb1");
```

```vb
Dim myDll As Assembly = _
    Assembly.Load("myDll, Version=1.0.0.1, Culture=neutral, PublicKeyToken=9b35aa32c18d4fb1")
```

Aşağıdaki [tanımlayıcı ad (sn. exe)](../../framework/tools/sn-exe-strong-name-tool.md) komutunu kullanarak, belirli bir derleme için ortak anahtar ve ortak anahtar belirtecinin onaltılık biçimini yazdırabilirsiniz:  

**sn-TP \<**  *derlemesi* **>**  

Ortak anahtar dosyanız varsa, bunun yerine aşağıdaki komutu kullanabilirsiniz (komut satırı seçeneğinde büyük/küçük harf farkını aklınızda bulabilirsiniz):  

**sn-TP \<**  *ortak anahtar dosyası* **>**  

## <a name="see-also"></a>Ayrıca bkz.

- [Tanımlayıcı adlı derlemeler oluşturma ve kullanma](create-use-strong-named.md)
