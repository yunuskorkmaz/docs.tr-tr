---
description: 'Hakkında daha fazla bilgi edinin: using deyimleri (Visual Basic)'
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
ms.openlocfilehash: fea77a441182b7c3ecac58d4fe7f1297a87f086c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740892"
---
# <a name="using-statement-visual-basic"></a>Using Deyimi (Visual Basic)

Bir bloğun başlangıcını bildirir `Using` ve isteğe bağlı olarak, blok denetimlerinin bulunduğu sistem kaynaklarını alır.

## <a name="syntax"></a>Syntax

```vb
Using { resourcelist | resourceexpression }
    [ statements ]
End Using
```

## <a name="parts"></a>Bölümler

|Süre|Tanım|  
|---|---|  
|`resourcelist`|Belirtmezseniz gereklidir `resourceexpression` . Bu `Using` blok tarafından denetimlerin, virgülle ayrılmış bir veya daha fazla sistem kaynağı listesi.|  
|`resourceexpression`|Belirtmezseniz gereklidir `resourcelist` . Bu blok tarafından denetlenebilecek bir sistem kaynağına başvuran başvuru değişkeni veya ifadesi `Using` .|  
|`statements`|İsteğe bağlı. `Using`Bloğun çalıştığı deyimler bloğu.|  
|`End Using`|Gereklidir. , `Using` Denetlediği tüm kaynakların bloğunun ve ayırdığından oluşan tanımı sonlandırır.|  

 Parçasındaki her kaynak `resourcelist` aşağıdaki söz dizimi ve bölümlere sahiptir:

 `resourcename As New resourcetype [ ( [ arglist ] ) ]`

 -veya-

 `resourcename As resourcetype = resourceexpression`

## <a name="resourcelist-parts"></a>resourceList bölümleri

|Süre|Tanım|  
|---|---|  
|`resourcename`|Gereklidir. Blok denetimlerinin bulunduğu bir sistem kaynağına başvuran başvuru değişkeni `Using` .|  
|`New`|Deyimin kaynağı alması durumunda gereklidir `Using` . Kaynağı zaten aldıysanız, ikinci söz dizimi alternatifini kullanın.|  
|`resourcetype`|Gereklidir. Kaynağın sınıfı. Sınıfın arabirimini uygulaması gerekir <xref:System.IDisposable> .|  
|`arglist`|İsteğe bağlı. Bir örneği oluşturmak için oluşturucuya geçirdiğiniz bağımsız değişkenlerin listesi `resourcetype` . Bkz. [parametre listesi](parameter-list.md).|  
|`resourceexpression`|Gereklidir. Gereksinimlerini karşılayan bir sistem kaynağına başvuran değişken veya ifade `resourcetype` . İkinci sözdizimi alternatif kullanırsanız, denetimi deyime geçirmeden önce kaynağı edinmeniz gerekir `Using` .|  
  
## <a name="remarks"></a>Açıklamalar

 Bazen kodunuzun dosya tanıtıcısı, COM sarmalayıcısı veya SQL bağlantısı gibi yönetilmeyen bir kaynak olması gerekir. Bir `Using` blok, kodunuz ile işiniz bittiğinde bir veya daha fazla kaynağı elden çıkarma garantisi verir. Bu, diğer kodun kullanması için kullanılabilir hale getirir.

 Yönetilen kaynaklar, .NET Framework atık toplayıcı (GC) tarafından, sizin bölümlemeden herhangi bir ek kodlama yapılmadan elden alınır. `Using`Yönetilen kaynaklar için bir bloğa ihtiyacınız yoktur. Ancak, `Using` çöp toplayıcıyı beklemek yerine, yönetilen bir kaynağın elden çıkarılmasını zorlamak için bir bloğu kullanmaya devam edebilirsiniz.

 Bir `Using` blok üç bölümden oluşur: alım, kullanım ve çıkarma.

- *Alım* , bir değişken oluşturma ve sistem kaynağına başvuracak şekilde başlatma anlamına gelir. `Using`Deyimde bir veya daha fazla kaynak alabilir ya da bloğu girmeden önce tam olarak bir kaynak alabilir ve bunu `Using` deyime sağlayabilirsiniz. Sağlarsanız `resourceexpression` , denetimi deyime geçirmeden önce kaynağı edinmeniz gerekir `Using` .

- *Kullanım* , kaynaklara erişmek ve bunlarla eylemler gerçekleştirmek anlamına gelir. Ve arasındaki deyimler `Using` , `End Using` kaynakların kullanımını temsil eder.

- *Aktiften çıkarma* , <xref:System.IDisposable.Dispose%2A> içindeki nesnesinde yöntemi çağırma anlamına gelir `resourcename` . Bu, nesnenin kaynaklarını düzgün bir şekilde sonlanmasına olanak tanır. `End Using`Bildiri, blok denetimindeki kaynakları ortadan kaldırır `Using` .

## <a name="behavior"></a>Davranış

 Bir `Using` blok, `Try` `Finally` `Try` bloğun kaynakları ve blok tarafından kullanıldığı bir... oluşturma gibi davranır `Finally` . Bu nedenle, bloğundan `Using` çıktığınızda bağımsız olarak blok kaynakların elden çıkarılmasını güvence altına alır. Bunun dışında, işlenmemiş bir özel durum durumunda da geçerlidir <xref:System.StackOverflowException> .

 İfadesiyle alınan her kaynak değişkeninin kapsamı `Using` `Using` bloğuyla sınırlıdır.

 Deyimde birden fazla sistem kaynağı belirtirseniz, efekt, bir diğeri `Using` içinde iç içe `Using` taşlarla aynı olur.

 `resourcename`İse `Nothing` , hiçbir çağrı <xref:System.IDisposable.Dispose%2A> yapılmaz ve hiçbir özel durum oluşturulmaz.

## <a name="structured-exception-handling-within-a-using-block"></a>Bir using bloğu Içinde yapılandırılmış özel durum Işleme

 Blok içinde oluşabilecek bir özel durumu işlemeniz gerekiyorsa `Using` , buna bir tamamlanmış `Try` ... `Finally` oluşturma ekleyebilirsiniz. `Using`Deyimin bir kaynağı alırken başarılı olmadığı durumu işlemeniz gerekiyorsa, olup olmadığını görmek için test edebilirsiniz `resourcename` `Nothing` .

## <a name="structured-exception-handling-instead-of-a-using-block"></a>Bir using bloğu yerine yapılandırılmış özel durum Işleme

 Kaynakların alımı üzerinde daha fazla denetime ihtiyacınız varsa veya blokta ek koda ihtiyacınız varsa `Finally` , `Using` bloğu bir... oluşturma olarak yeniden yazabilirsiniz `Try` `Finally` . Aşağıdaki örnek, `Try` `Using` alma ve aktiften çıkarma ile eşdeğer olan iskelet ve kurulumlarını gösterir `resource` .

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
> Bloğun içindeki kod `Using` nesneyi `resourcename` başka bir değişkene atamamalıdır. `Using`Bloğundan çıktığınızda, kaynak atılmış olur ve diğer değişken işaret ettiği kaynağa erişemez.

## <a name="example"></a>Örnek

 Aşağıdaki örnek, log.txt adında bir dosya oluşturur ve dosyaya iki satırlık metin yazar. Örnek ayrıca aynı dosyayı okur ve metin satırlarını görüntüler:

 <xref:System.IO.TextWriter>Ve <xref:System.IO.TextReader> sınıfları <xref:System.IDisposable> arabirimini uygulamadığından, kod, `Using` yazma ve okuma işlemlerinden sonra dosyanın doğru şekilde kapatılmasını sağlamak için deyimlerini kullanabilir.

 [!code-vb[VbVbalrStatements#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#50)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IDisposable>
- [Try...Catch...Finally Deyimi](try-catch-finally-statement.md)
- [Nasıl yapılır: Bir Sistem Kaynağını Atma](../../programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md)
