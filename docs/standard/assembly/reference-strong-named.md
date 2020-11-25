---
title: 'Nasıl yapılır: tanımlayıcı adlı bir derlemeye başvurma'
description: Bu makalede, derleme zamanında veya çalışma zamanında tanımlayıcı adlı bir .NET derlemesinde türlerin veya kaynakların nasıl başvurulacağını gösterilmektedir.
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies, compile-time references
- compile-time assembly referencing
- assemblies [.NET], strong-named
- assembly binding, strong-named
ms.assetid: 4c6a406a-b5eb-44fa-b4ed-4e95bb95a813
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 919e4f4cf467e8fc28c3d007963393dad134ab57
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724058"
---
# <a name="how-to-reference-a-strong-named-assembly"></a>Nasıl yapılır: tanımlayıcı adlı bir derlemeye başvurma

Tanımlayıcı adlı bir derlemede tür veya kaynaklara başvurma işlemi genellikle saydamdır. Başvuruyu derleme zamanında (erken bağlama) veya çalışma zamanında yapabilirsiniz.  
  
Derleyiciye derlenen derlemenin başka bir derlemeye açıkça başvuruda bulunduğunu belirttiğinizde derleme zamanı başvurusu oluşur. Derleme zamanı başvurusu kullandığınızda, derleyici hedeflenen tanımlayıcı adlı derlemenin ortak anahtarını otomatik olarak alır ve derlenen derlemenin derleme başvurusuna koyar.
  
> [!NOTE]
> Tanımlayıcı adlı bir derleme, yalnızca diğer tanımlayıcı adlı derlemelerden türleri kullanabilir. Aksi takdirde, tanımlayıcı adlı derlemenin güvenliği tehlikeye girebilir.  
  
## <a name="make-a-compile-time-reference-to-a-strong-named-assembly"></a>Tanımlayıcı adlı bir derlemeye derleme zamanı başvurusu yapma  

Komut isteminde aşağıdaki komutu yazın:  

\<*compiler command*>**/Reference:**\<*assembly name*>  

Bu komutta *derleyici komutu* , kullanmakta olduğunuz dilin derleyici komutu ve *derleme adı* , başvurulmakta olan tanımlayıcı adlı derlemenin adıdır. Ayrıca, bir kitaplık derlemesi oluşturmak için **/t: Library** seçeneği gibi diğer derleyici seçeneklerini de kullanabilirsiniz.  

Aşağıdaki örnek, *MyAssembly.cs* adlı bir kod modülünden *myLibAssembly.dll* adlı tanımlayıcı adlı bir derlemeye başvuran *myAssembly.dll* adlı bir derleme oluşturur.  

```cmd
csc /t:library myAssembly.cs /reference:myLibAssembly.dll  
```  

## <a name="make-a-run-time-reference-to-a-strong-named-assembly"></a>Tanımlayıcı adlı bir derlemeye çalışma zamanı başvurusu yapma  
  
Tanımlayıcı adlı bir derlemeye çalışma zamanı başvurusu yaptığınızda (örneğin, veya yöntemini kullanarak), <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> başvurulan tanımlayıcı adlı derlemenin görünen adını kullanmanız gerekir. Görünen adın sözdizimi aşağıdaki gibidir:  

\<*assembly name*>**,** \<*version number*>**,** \<*culture*>**,** \<*public key token*>  

Örnek:  

```console
myDll, Version=1.1.0.0, Culture=en, PublicKeyToken=03689116d3a4ae33
```  

Bu örnekte, `PublicKeyToken` ortak anahtar belirtecinin onaltılı biçimidir. Kültür değeri yoksa kullanın `Culture=neutral` .  

Aşağıdaki kod örneği, bu bilgileri yöntemiyle nasıl kullanacağınızı gösterir <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> .  

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

Aşağıdaki [tanımlayıcı ad (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md) komutunu kullanarak, belirli bir derleme için ortak anahtar ve ortak anahtar belirtecinin onaltılık biçimini yazdırabilirsiniz:  

**sn-TP \<** *assembly* **>**  

Ortak anahtar dosyanız varsa, bunun yerine aşağıdaki komutu kullanabilirsiniz (komut satırı seçeneğinde büyük/küçük harf farkını aklınızda bulabilirsiniz):  

**sn-TP \<** *public key file* **>**  

## <a name="see-also"></a>Ayrıca bkz.

- [Tanımlayıcı adlı derlemeler oluşturma ve kullanma](create-use-strong-named.md)
