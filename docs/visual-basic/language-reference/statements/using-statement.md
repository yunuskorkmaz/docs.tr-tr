---
title: Using Deyimi (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.using
helpviewer_keywords:
- resource disposal
- Try...Catch...Finally statements, equivalent to Using statement
- resources [Visual Basic], disposing
- Using statement [Visual Basic]
ms.assetid: 665d1580-dd54-4e96-a9a9-6be2a68948f1
caps.latest.revision: "36"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ed9cc0d04c89eac1fe342a0924dd89bb1e258a11
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="using-statement-visual-basic"></a>Using Deyimi (Visual Basic)
Başlangıcı bildiren bir `Using` engelleme ve isteğe bağlı olarak blok denetimleri sistem kaynakları alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Using { resourcelist | resourceexpression }  
    [ statements ]  
End Using  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`resourcelist`|Değil sağladığınız varsa gerekli `resourceexpression`. Listesinde bir veya daha fazla sistem kaynaklarının bu `Using` engellemek denetimleri, virgülle ayrılmış.|  
|`resourceexpression`|Değil sağladığınız varsa gerekli `resourcelist`. Başvuru değişkenini veya ifadesi bu tarafından denetlenmesi için bir sistem kaynağa başvuran `Using` bloğu.|  
|`statements`|İsteğe bağlı. İfadeler bloğu, `Using` engelleme çalıştırır.|  
|`End Using`|Gerekli. Tanımını sonlandırır `Using` bloğu ve denetlediği tüm kaynakları siler.|  
  
 Her bir kaynağın `resourcelist` bölümü aşağıdaki söz dizimini ve bölümleri sahiptir:  
  
 `resourcename As New resourcetype [ ( [ arglist ] ) ]`  
  
 veya  
  
 `resourcename As resourcetype = resourceexpression`  
  
## <a name="resourcelist-parts"></a>resourcelist bölümleri  
  
|Terim|Tanım|  
|---|---|  
|`resourcename`|Gerekli. Bir sistem kaynağı başvuruyor başvuru değişkeni, `Using` engelleme kontrol eder.|  
|`New`|Gerekli olursa `Using` deyimi kaynak edinir. Kaynak zaten aldıysanız, ikinci sözdizimi alternatif kullanın.|  
|`resourcetype`|Gerekli. Kaynak sınıfı. Sınıf uygulamalıdır <xref:System.IDisposable> arabirimi.|  
|`arglist`|İsteğe bağlı. Örneği oluşturmak için oluşturucusuna geçirerek bağımsız değişkenler listesi `resourcetype`. Bkz: [parametre listesi](../../../visual-basic/language-reference/statements/parameter-list.md).|  
|`resourceexpression`|Gerekli. Değişken veya başvuran gereksinimlerini karşılayan bir sistem kaynağı deyim `resourcetype`. İkinci sözdizimi alternatif kullanırsanız, denetimine geçirmeden önce kaynak almalıdır `Using` deyimi.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bazen bir dosya tanıtıcısı, COM sarmalayıcı veya bir SQL bağlantısı gibi yönetilmeyen bir kaynak kodunuzu gerektirir. A `Using` blok kodunuzu bunlarla tamamlandığında, bir veya daha fazla gibi kaynakların elden garanti eder. Bu bunları kullanmak başka bir kod için kullanılabilir hale getirir.  
  
 Yönetilen kaynaklar için .NET Framework Atık toplayıcısının (GC) tarafından hiçbir ek kodlama yapmanız olmadan elden. İhtiyacınız olmayan bir `Using` yönetilen kaynaklar için bloğu. Ancak, kullanmaya devam edebilirsiniz bir `Using` için atık toplayıcısını beklemek yerine yönetilen bir kaynağın elden zorlamak için blok.  
  
 A `Using` blok sahip üç bölümden: edinme, kullanım ve elden.  
  
-   *Alım* bir değişken oluşturma ve bu sistem kaynağı başvurmak için başlatma anlamına gelir. `Using` Deyimi bir veya daha fazla kaynak elde veya blok girmeden önce tam olarak bir kaynak almak ve ona tedarik `Using` deyimi. Sağladığınız varsa `resourceexpression`, kaynak denetimine geçirmeden önce almalıdır `Using` deyimi.  
  
-   *Kullanım* kaynaklara erişme ve bunlarla gerçekleştirme anlamına gelir. Arasında deyimleri `Using` ve `End Using` kaynak kullanımını temsil eder.  
  
-   *Elden* çağırma anlamına gelir <xref:System.IDisposable.Dispose%2A> yöntemi nesnedeki `resourcename`. Bu, düzgün bir şekilde kaynaklarını sonlandırmak nesne sağlar. `End Using` Deyimi siler altında kaynakların `Using` bloğun denetim.  
  
## <a name="behavior"></a>Davranış  
 A `Using` engelleme davranacağını gibi bir `Try`... `Finally` hangi yapısında `Try` bloğu kaynakları kullanır ve `Finally` blok bunları siler. Bu nedenle, `Using` blok blok çıkmak nasıl olsun bu kaynakların elden güvence altına alır. Bu bile işlenmeyen bir özel durum söz konusu olduğunda, geçerlidir dışında bir <xref:System.StackOverflowException>.  
  
 Tarafından alınan her kaynak değişkenin kapsamını `Using` deyimi sınırlıdır `Using` bloğu.  
  
 Birden fazla sistem kaynağında belirtirseniz `Using` deyimi, etkisi ise aynı iç içe gibi `Using` bir diğeri içindeki engeller.  
  
 Varsa `resourcename` olan `Nothing`, hiçbir çağrısına <xref:System.IDisposable.Dispose%2A> yapılmış ve hiçbir özel durum.  
  
## <a name="structured-exception-handling-within-a-using-block"></a>Yapılandırılmış özel durum işleme kullanan bir blokta  
 İçinde oluşabilecek bir özel durum işleme gerekiyorsa `Using` bloğu, bir tam ekleyebilirsiniz `Try`... `Finally` ona oluşturma. Servis talebi işlemek gerekirse burada `Using` deyimi bir kaynak alınırken başarılı değil, olup olmadığını sınayabilirsiniz `resourcename` olan `Nothing`.  
  
## <a name="structured-exception-handling-instead-of-a-using-block"></a>Yapılandırılmış özel durum işleme kullanan bir blok yerine  
 Kaynakları alımını üzerinde daha hassas denetim gerekir veya ek kod, ihtiyacınız varsa `Finally` bloğu yeniden yazana `Using` olarak engelleme bir `Try`... `Finally` oluşturma. Aşağıdaki örnek, iskelet gösterir `Try` ve `Using` edinme ve elden eşdeğer kurulumlarını `resource`.  
  
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
>  Kod içinde `Using` blok nesnesinde değil atamanız `resourcename` başka bir değişkene. Çıktığınızda `Using` bloğu, kaynak kapatılır ve diğer değişkenin işaret ettiği kaynağına erişemiyor.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek log.txt adlı ve iki satırlık bir metin dosyasına yazan bir dosya oluşturur. Örnek ayrıca, aynı dosyasını okur ve metin satırlarını görüntüler.  
  
 Çünkü <xref:System.IO.TextWriter> ve <xref:System.IO.TextReader> sınıfları uygulama <xref:System.IDisposable> arabirimi kodu kullanabilirsiniz `Using` deyimleri dosyanın doğru sonra yazma kapalı ve okuma işlemlerini emin olun.  
  
 [!code-vb[VbVbalrStatements#50](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/using-statement_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IDisposable>  
 [Try... Catch... Finally ifadesi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [Nasıl yapılır: bir sistem kaynağını atma](../../../visual-basic/programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md)
