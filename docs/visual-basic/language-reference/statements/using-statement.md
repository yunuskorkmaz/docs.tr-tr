---
title: Using Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.using
helpviewer_keywords:
- resource disposal
- Try...Catch...Finally statements, equivalent to Using statement
- resources [Visual Basic], disposing
- Using statement [Visual Basic]
ms.assetid: 665d1580-dd54-4e96-a9a9-6be2a68948f1
ms.openlocfilehash: 6ec0e228b3898f66f27e322b5db2dd7f3bf3d7d6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352766"
---
# <a name="using-statement-visual-basic"></a>Using Deyimi (Visual Basic)

`Using` bloğunun başlangıcını bildirir ve isteğe bağlı olarak blok denetimlerinin bulunduğu sistem kaynaklarını alır.

## <a name="syntax"></a>Sözdizimi

```vb
Using { resourcelist | resourceexpression }
    [ statements ]
End Using
```

## <a name="parts"></a>Bölümler

|Terim|Tanım|  
|---|---|  
|`resourcelist`|`resourceexpression`vermezseniz gereklidir. Bu `Using`, denetimleri virgülle ayırarak bir veya daha fazla sistem kaynağı listesi.|  
|`resourceexpression`|`resourcelist`vermezseniz gereklidir. Bu `Using` bloğunun denetimine yönelik bir sistem kaynağını işaret eden başvuru değişkeni veya ifadesi.|  
|`statements`|İsteğe bağlı. `Using` bloğunun çalıştığı deyimler bloğu.|  
|`End Using`|Gerekli. `Using` bloğunun tanımını sonlandırır ve denetlediği tüm kaynakların ayırt etmesidir.|  

 `resourcelist` bölümündeki her kaynak aşağıdaki söz dizimi ve bölümlere sahiptir:

 `resourcename As New resourcetype [ ( [ arglist ] ) ]`

 veya

 `resourcename As resourcetype = resourceexpression`

## <a name="resourcelist-parts"></a>resourceList bölümleri

|Terim|Tanım|  
|---|---|  
|`resourcename`|Gerekli. `Using` bloğunun denetlediği bir sistem kaynağını ifade eden başvuru değişkeni.|  
|`New`|`Using` deyimin kaynağı alması durumunda gereklidir. Kaynağı zaten aldıysanız, ikinci söz dizimi alternatifini kullanın.|  
|`resourcetype`|Gerekli. Kaynağın sınıfı. Sınıfın <xref:System.IDisposable> arabirimini uygulaması gerekir.|  
|`arglist`|İsteğe bağlı. `resourcetype`bir örneğini oluşturmak için oluşturucuya geçirdiğiniz bağımsız değişkenlerin listesi. Bkz. [parametre listesi](parameter-list.md).|  
|`resourceexpression`|Gerekli. `resourcetype`gereksinimlerini karşılayan bir sistem kaynağına başvuran değişken veya ifade. İkinci sözdizimi alternatif kullanırsanız, denetimi `Using` bildirimine geçirmeden önce kaynağı edinmeniz gerekir.|  
  
## <a name="remarks"></a>Açıklamalar

 Bazen kodunuzun dosya tanıtıcısı, COM sarmalayıcısı veya SQL bağlantısı gibi yönetilmeyen bir kaynak olması gerekir. `Using` bir blok, kodunuz ile işiniz bittiğinde bir veya daha fazla kaynağı elden çıkarma garantisi verir. Bu, diğer kodun kullanması için kullanılabilir hale getirir.

 Yönetilen kaynaklar, .NET Framework atık toplayıcı (GC) tarafından, sizin bölümlemeden herhangi bir ek kodlama yapılmadan elden alınır. Yönetilen kaynaklar için `Using` bloğuna ihtiyacınız yoktur. Ancak, bir `Using` bloğunu, atık toplayıcıyı beklemek yerine, yönetilen bir kaynağın elden çıkarılmasını zorlamak için kullanmaya devam edebilirsiniz.

 `Using` bloğu üç bölümden oluşur: alma, kullanım ve aktiften çıkarma.

- *Alım* , bir değişken oluşturma ve sistem kaynağına başvuracak şekilde başlatma anlamına gelir. `Using` bildiriminde bir veya daha fazla kaynak edinebilir veya bloğu girmeden önce tam olarak bir kaynak alabilir ve bunu `Using` bildirimine sağlayabilirsiniz. `resourceexpression`sağlarsanız, denetimi `Using` bildirimine geçirmeden önce kaynağı edinmeniz gerekir.

- *Kullanım* , kaynaklara erişmek ve bunlarla eylemler gerçekleştirmek anlamına gelir. `Using` ve `End Using` arasındaki deyimler, kaynakların kullanımını temsil eder.

- *Aktiften çıkarma* , `resourcename`nesne üzerinde <xref:System.IDisposable.Dispose%2A> yönteminin çağrılması anlamına gelir. Bu, nesnenin kaynaklarını düzgün bir şekilde sonlanmasına olanak tanır. `End Using` deyimleri, `Using` bloğunun denetimindeki kaynakları ortadan kaldırır.

## <a name="behavior"></a>Davranış

 `Using` bloğu, `Try` bloğunun kaynakları kullandığı ve `Finally` bloğunun oluşturduğu bir `Try`...`Finally` oluşturma gibi davranır. Bu nedenle, `Using` bloğu, bloğundan çıktığınızda bağımsız olarak kaynakların elden çıkarılmasını garanti eder. Bu, <xref:System.StackOverflowException>hariç, işlenmemiş bir özel durum durumunda da geçerlidir.

 `Using` ifadesiyle alınan her kaynak değişkeninin kapsamı `Using` bloğuyla sınırlıdır.

 `Using` bildiriminde birden fazla sistem kaynağı belirtirseniz, efekt, iç içe geçmiş `Using` bloklarla aynı olur.

 `resourcename` `Nothing`, <xref:System.IDisposable.Dispose%2A> çağrısı yapılmaz ve hiçbir özel durum oluşturulmaz.

## <a name="structured-exception-handling-within-a-using-block"></a>Bir using bloğu Içinde yapılandırılmış özel durum Işleme

 `Using` bloğunda oluşabilecek bir özel durumu işlemeniz gerekiyorsa, buna bir tamamen `Try`...`Finally` oluşturma ekleyebilirsiniz. `Using` deyimin kaynak alma işleminin başarılı olmadığı durumu işlemeniz gerekiyorsa, `resourcename` `Nothing`olup olmadığını görmek için test edebilirsiniz.

## <a name="structured-exception-handling-instead-of-a-using-block"></a>Bir using bloğu yerine yapılandırılmış özel durum Işleme

 Kaynakların alımı üzerinde daha fazla denetime ihtiyacınız varsa veya `Finally` bloğunda ek koda ihtiyacınız varsa `Using` bloğunu `Try`...`Finally` oluşturma olarak yeniden yazabilirsiniz. Aşağıdaki örnek, `resource`alımı ve aktiften çıkarılması ile eşdeğer olan iskelet `Try` ve `Using` kurulumlarını gösterir.

```vb
Using resource As New resourceType
    ' Insert code to work with resource.
End Using

' For the acquisition and disposal of resource, the following  
' Try construction is equivalent to the Using block.
Dim resource As New resourceType
Try
    ' Insert code to work with resource.
Finally
    If resource IsNot Nothing Then
        resource.Dispose()
    End If
End Try
```

> [!NOTE]
> `Using` bloğunun içindeki kod, `resourcename` nesneyi başka bir değişkene atamamalıdır. `Using` bloğundan çıktığınızda, kaynak atılmış olur ve diğer değişken işaret ettiği kaynağa erişemez.

## <a name="example"></a>Örnek

 Aşağıdaki örnek, log. txt adlı bir dosya oluşturur ve dosyaya iki satırlık metin yazar. Örnek ayrıca aynı dosyayı okur ve metin satırlarını görüntüler:

 <xref:System.IO.TextWriter> ve <xref:System.IO.TextReader> sınıfları <xref:System.IDisposable> arabirimini uygulamadığından, kod, dosyanın yazma ve okuma işlemlerinden sonra doğru şekilde kapatılmasını sağlamak için `Using` deyimlerini kullanabilir.

 [!code-vb[VbVbalrStatements#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#50)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IDisposable>
- [Try...Catch...Finally Deyimi](try-catch-finally-statement.md)
- [Nasıl yapılır: Bir Sistem Kaynağını Atma](../../programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md)
