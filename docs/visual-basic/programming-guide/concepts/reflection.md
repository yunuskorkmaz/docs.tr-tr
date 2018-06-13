---
title: Yansıma (Visual Basic)
ms.date: 07/20/2015
ms.assetid: d991bc0f-d16a-4ac5-9351-70e5c5b9891b
ms.openlocfilehash: f47f78ff9989fc44ad46b66a447061c3fa84a86e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33646695"
---
# <a name="reflection-visual-basic"></a>Yansıma (Visual Basic)
Yansıma nesneleri sağlar (tür <xref:System.Type>) derlemeler, modüller ve türleri açıklanmaktadır. Yansıma dinamik olarak bir türünün bir örneği oluşturmak, var olan bir nesne için bağ türü veya varolan bir nesneden türünü almak ve onun yöntemleri çağırma veya özellikleri ve alanları erişim için kullanabilirsiniz. Kodunuzda öznitelikleri kullanıyorsanız, yansıma erişmesine olanak sağlar. Daha fazla bilgi için bkz: [öznitelikleri](../../../standard/attributes/index.md).  
  
 Yansıma statik yöntemini kullanarak basit bir örneği burada verilmiştir `GetType` - tüm türlerinden tarafından devralınan `Object` temel sınıfı - değişken türünü almak için:  
  
```vb  
' Using GetType to obtain type information:  
Dim i As Integer = 42  
Dim type As System.Type = i.GetType()  
System.Console.WriteLine(type)  
```  
  
 Çıktısı şöyledir:  
  
 `System.Int32`  
  
 Aşağıdaki örnek yansıma yüklenen derlemenin tam adını almak için kullanır.  
  
```vb  
' Using Reflection to get information from an Assembly:  
Dim info As System.Reflection.Assembly = GetType(System.Int32).Assembly  
System.Console.WriteLine(info)  
```  
  
 Çıktısı şöyledir:  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
## <a name="reflection-overview"></a>Yansıma genel bakış  
 Yansıma, aşağıdaki durumlarda yararlıdır:  
  
-   Öznitelikleri programınızın meta verilerde erişmek olduğunda. Daha fazla bilgi için bkz: [öznitelikleri saklı alma bilgi](../../../standard/attributes/retrieving-information-stored-in-attributes.md).  
  
-   İncelenerek ve derlemedeki türleri oluşturmak için.  
  
-   Çalışma zamanında yeni türleri oluşturmak için. Sınıflarda kullanmak <xref:System.Reflection.Emit>.  
  
-   Çalışma zamanında oluşturulan türleri yöntemlere erişme geç bağlama gerçekleştirmek için. Konusuna [dinamik olarak yükleme ve türleri kullanma](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).  
  
## <a name="related-sections"></a>İlgili Bölümler  
 Daha fazla bilgi için:  
  
-   [Yansıma](../../../framework/reflection-and-codedom/reflection.md)  
  
-   [Tür Bilgilerini Görüntüleme](../../../framework/reflection-and-codedom/viewing-type-information.md)  
  
-   [Yansıma ve Genel Türler](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
  
-   <xref:System.Reflection.Emit>  
  
-   [Özniteliklerde Depolanan Bilgileri Alma](../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic programlama kılavuzu](../../../visual-basic/programming-guide/index.md)  
 [Ortak Dil Çalışma Zamanı Modülündeki Bütünleştirilmiş Kodlar](../../../framework/app-domains/assemblies-in-the-common-language-runtime.md)
