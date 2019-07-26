---
title: Erişen örnek bir arabirim türü olduğundan geç bağlanan tekrar yükleme çözümü '<procedurename>' öğesine uygulanamaz
ms.date: 07/20/2015
f1_keywords:
- vbc30933
- bc30933
helpviewer_keywords:
- overload resolution [Visual Basic], with late-bound argument
- BC30933
ms.assetid: 8182eea0-dd34-4d6e-9ca0-41d8713e9dc4
ms.openlocfilehash: 1fe3c4a29b542302b3615459142a3c565aa8244f
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68513018"
---
# <a name="latebound-overload-resolution-cannot-be-applied-to-procedurename-because-the-accessing-instance-is-an-interface-type"></a>Erişen örnek bir arabirim türü olduğundan, geç bağlanan\<aşırı yükleme çözümlemesi ' procedurename > ' öğesine uygulanamaz

Derleyici aşırı yüklenmiş bir özellik veya yordama yönelik bir başvuruyu çözümlemeye çalışıyor, ancak bir bağımsız değişken türünde `Object` olduğu ve başvuran nesnenin bir arabirimin veri türü olduğu için başvuru başarısız olur. `Object` Bağımsız değişkeni, derleyicinin başvuruyu geç bağlantılı olarak çözmeye zorlar.

Bu koşullarda derleyici, temel alınan arabirim yerine uygulama sınıfı aracılığıyla aşırı yüklemeyi çözer. Sınıf, aşırı yüklenmiş sürümlerden birini yeniden adlandırdığında, adı farklı olduğu için derleyici bu sürümü bir aşırı yükleme olarak kabul etmez. Bu işlem, derleyicinin başvuruyu çözümlemek için doğru seçim yapmış olabileceği zaman yeniden adlandırılan sürümü yoksaymasına neden olur.

**Hata KIMLIĞI:** BC30933

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- Bağımsız değişkenini `CType`,çağırmak istediğiniz aşırı yüklemenin imzasıyla belirtilen türe dönüştürmek için kullanın. `Object`

  Başvuran nesneyi temel arabirime dönüştürmeye yardımcı olmadığına unutmayın. Bu hatadan kaçınmak için bağımsız değişkeni atamalısınız.

## <a name="example"></a>Örnek

Aşağıdaki örnek, derleme zamanında bu hataya neden olan `Sub` aşırı yüklenmiş bir yordamın çağrısını gösterir.

```vb
Module m1
    Interface i1
        Sub s1(ByVal p1 As Integer)
        Sub s1(ByVal p1 As Double)
    End Interface
    Class c1
        Implements i1
        Public Overloads Sub s1(ByVal p1 As Integer) Implements i1.s1
        End Sub
        Public Overloads Sub s2(ByVal p1 As Double) Implements i1.s1
        End Sub
    End Class
    Sub Main()
        Dim refer As i1 = New c1
        Dim o1 As Object = 3.1415
        ' The following reference is INVALID and causes a compiler error.
        refer.s1(o1)
    End Sub
End Module
```

Önceki örnekte, derleyici çağrıyı `s1` yazıldığı gibi olarak izin verirdi, çözümleme arabirimi `i1`yerine sınıfı `c1` aracılığıyla gerçekleşir. Bu, tarafından `s2` `c1` tanımlandığıgibidoğruseçimolsada,derleyicininadıfarklıolduğuiçingözönündebulundurmadığı`i1`anlamına gelir.

Çağrıyı aşağıdaki kod satırlarından birine değiştirerek hatayı düzeltebilirsiniz:

```vb
refer.s1(CType(o1, Integer))
refer.s1(CType(o1, Double))
```

Önceki kod satırlarının her biri `Object` değişkeni `o1` açıkça aşırı yüklemeler için tanımlanan parametre türlerinden birine açıkça yayınlar.

## <a name="see-also"></a>Ayrıca bkz.

- [Yordam Aşırı Yüklemesi](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)
- [Aşırı Yükleme Çözümü](../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)
- [CType İşlevi](../../../visual-basic/language-reference/functions/ctype-function.md)
