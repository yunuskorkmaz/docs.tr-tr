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
ms.openlocfilehash: 281cfa6507d293658e436a95a5ded0174154a13c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59301028"
---
# <a name="how-to-reference-a-strong-named-assembly"></a>Nasıl yapılır: Tanımlayıcı Adlı Bir Derlemeye Başvurma
Türleri veya bir katı adlı derleme kaynaklara başvuran işlemi genellikle saydamdır. Başvuru (erken bağlama) derleme zamanında ya da çalışma zamanında yapabilirsiniz.  
  
 Derleyiciye belirttiğinizde, derlemenizi açıkça başka bir derlemeye başvuran bir derleme zamanı başvurusu gerçekleşir. Derleme zamanı başvuran kullandığınızda, derleyici otomatik olarak hedeflenen tanımlayıcı adlı bütünleştirilmiş kodunun ortak anahtarı alır ve derlenmiş bütünleştirilmiş kod derleme başvurusu yerleştirir.  
  
> [!NOTE]
>  Tanımlayıcı adlı bütünleştirilmiş kod, yalnızca diğer güçlü adlı derlemelere türlerinden kullanabilirsiniz. Aksi takdirde, tanımlayıcı adlı bütünleştirilmiş kodun güvenliğini tehlikeye.  
  
### <a name="to-make-a-compile-time-reference-to-a-strong-named-assembly"></a>Tanımlayıcı adlı bütünleştirilmiş kod derleme zamanı başvuru yapma  
  
1. Komut satırında, aşağıdaki komutu yazın:  
  
     \<*derleyici komut*> **/reference:**\<*derleme adı*>  
  
     Bu komutta *derleyici komut* derleyici komut kullandığınız dil ve *derleme adı* başvurulan tanımlayıcı adlı bütünleştirilmiş kodun adı. Gibi diğer derleyici seçenekleri kullanabilirsiniz **/t:library** Kitaplık derlemesi oluşturmak için seçeneği.  
  
 Aşağıdaki örnekte adlı bir derleme oluşturur `myAssembly.dll` adlı bir tanımlayıcı adlı bütünleştirilmiş kod başvuruları `myLibAssembly.dll` adlı kod modülünde `myAssembly.cs`.  
  
```  
csc /t:library myAssembly.cs /reference:myLibAssembly.dll  
```  
  
### <a name="to-make-a-run-time-reference-to-a-strong-named-assembly"></a>Tanımlayıcı adlı bütünleştirilmiş kod çalışma zamanı başvuru yapma  
  
1. Bir çalışma zamanı başvurusu bir katı adlı derleme yaptığınızda (kullanarak örneğin, <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> veya <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> yöntemi), başvurulan kesin adlandırılmış derlemenin görünen adını kullanmanız gerekir. Bir görünen ad sözdizimi aşağıdaki gibidir:  
  
     \<*derleme adı*>**,** \< *sürüm numarası*>**,** \< *kültürü*  > **,** \< *ortak anahtar belirteci*>  
  
     Örneğin:  
  
    ```  
    myDll, Version=1.1.0.0, Culture=en, PublicKeyToken=03689116d3a4ae33   
    ```  
  
     Bu örnekte, `PublicKeyToken` onaltılık ortak anahtar belirteci biçimindedir. Kültür değer yoksa kullanın `Culture=neutral`.  
  
 Aşağıdaki kod örneği bu bilgileri ile nasıl kullanacağınızı gösterir <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemi.  
  
 [!code-cpp[Assembly.Load1#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Assembly.Load1/CPP/load2.cpp#3)]
 [!code-csharp[Assembly.Load1#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Assembly.Load1/CS/load2.cs#3)]
 [!code-vb[Assembly.Load1#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Assembly.Load1/VB/load2.vb#3)]  
  
 Aşağıdakileri kullanarak, belirli bir derleme için ortak anahtar ve ortak anahtar belirteci on altılık biçimde yazdırabilir [tanımlayıcı ad (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) komutu:  
  
 **sn - Tp \<**  *derleme* **>**  
  
 Bunun yerine ortak anahtar dosyası varsa, aşağıdaki komutu kullanabilirsiniz (komut satırı seçeneğini durumda farka dikkat edin):  
  
 **sn - tp \<**  *ortak anahtar dosyası* **>**  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kesin Adlandırılmış Bütünleştirilmiş Kodlar Oluşturma ve Kullanma](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
