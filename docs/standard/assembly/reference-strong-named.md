---
title: 'Nasıl yapılsın: Güçlü bir derlemeye başvuru'
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies, compile-time references
- compile-time assembly referencing
- assemblies [.NET Framework], strong-named
- assembly binding, strong-named
ms.assetid: 4c6a406a-b5eb-44fa-b4ed-4e95bb95a813
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: adda4ed2ab5c59e3518b8e724044529a79840ad0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78156484"
---
# <a name="how-to-reference-a-strong-named-assembly"></a>Nasıl yapılsın: Güçlü bir derlemeye başvuru
Güçlü adlandırılmış bir derlemede başvuru türleri veya kaynakları için işlem genellikle saydamdır. Başvuruyu derleme zamanında (erken bağlama) veya çalışma zamanında yapabilirsiniz.  
  
Derleyiciye derlemesi için derlenecek derlemenin başka bir derlemeye açıkça atıfta bulunulmasını belirttiğiniz zaman derleme zamanı başvurusu oluşur. Derleme zamanı başvurularını kullandığınızda, derleyici hedeflenen güçlü adı verilen derlemenin ortak anahtarını otomatik olarak alır ve derlenen derlemenin derleme başvurusuna yerleştirir.
  
> [!NOTE]
> Güçlü adlandırılmış derleme yalnızca diğer güçlü adlandırılmış derlemelerden türleri kullanabilir. Aksi takdirde, güçlü adlı derlemenin güvenliği tehlikeye girer.  
  
## <a name="make-a-compile-time-reference-to-a-strong-named-assembly"></a>Güçlü adlandırılmış derlemeiçin derleme zamanı başvurusu yapma  

Komut isteminde aşağıdaki komutu yazın:  

\<*derleyici komutu*> **/başvuru:**\<*derleme adı*>  

Bu komutta *derleyici komutu* kullandığınız dilin derleyici komutudur ve *derleme adı* başvurulan güçlü adlandırılmış derlemenin adıdır. Kitaplık derlemesi oluşturmak için **/t:kitaplık** seçeneği gibi diğer derleyici seçeneklerini de kullanabilirsiniz.  

Aşağıdaki örnek, *myAssembly.cs*adlı bir kod modülünden *myLibAssembly.dll* adlı güçlü bir derlemeye başvuran *myAssembly.dll* adlı bir derleme oluşturur.  

```cmd
csc /t:library myAssembly.cs /reference:myLibAssembly.dll  
```  

## <a name="make-a-run-time-reference-to-a-strong-named-assembly"></a>Güçlü adlandırılmış derlemeye çalışma zamanı başvurusu yapma  
  
Örneğin, <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> güçlü <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> adlı bir derlemeye çalışma zamanı başvurusu yaptığınızda, örneğin veya yöntemi ni kullanarak, başvurulan güçlü adlandırılmış derlemenin görüntü adını kullanmanız gerekir. Görüntü adının sözdizimi aşağıdaki gibidir:  

\<*derleme adı*>**,** \< *sürüm numarası*>**,** \< *kültür*>**,** \< *ortak anahtar belirteci*>  

Örnek:  

```console
myDll, Version=1.1.0.0, Culture=en, PublicKeyToken=03689116d3a4ae33
```  

Bu örnekte, `PublicKeyToken` ortak anahtar belirteci hexadecimal şeklidir. Kültür değeri yoksa, kullanın. `Culture=neutral`  

Aşağıdaki kod örneği, yöntemle bu <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> bilgilerin nasıl kullanılacağını gösterir.  

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

Aşağıdaki [Güçlü Ad (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md) komutunu kullanarak belirli bir derleme için ortak anahtarın ve ortak anahtar belirtecisinin hexadecimal biçimini yazdırabilirsiniz:  

**sn \< -Tp** *montajı***>**  

Ortak anahtar dosyanız varsa, bunun yerine aşağıdaki komutu kullanabilirsiniz (komut satırı seçeneğindeki duruma ilişkin farkı not edin):  

**sn -tp \< ** *genel anahtar dosyası***>**  

## <a name="see-also"></a>Ayrıca bkz.

- [Tanımlayıcı adlı derlemeler oluşturma ve kullanma](create-use-strong-named.md)
