---
title: On Error Deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.OnError
helpviewer_keywords:
- Visual Basic code, control flow
- Resume Next statement [Visual Basic]
- errors [Visual Basic], trapping
- error handling, On Error statement
- Next statement [Visual Basic], On Error
- control flow [Visual Basic], branching
- Error keyword [Visual Basic]
- execution [Visual Basic], conditional
- Resume statement [Visual Basic], and On Error statement
- Error statement [Visual Basic], and On Error statement
- GoTo statement [Visual Basic], and On Error statement
- branching [Visual Basic], on error
- conditional statements [Visual Basic], On Error
- On Error statement [Visual Basic], syntax
- On keyword [Visual Basic]
- run-time errors [Visual Basic], handling
- On Error statement [Visual Basic]
ms.assetid: ff947930-fb84-40cf-bd66-1ea219561d5c
ms.openlocfilehash: 5dc432f8e62430d48954b2c049cab3ebae4d442e
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57203749"
---
# <a name="on-error-statement-visual-basic"></a>On Error Deyimi (Visual Basic)
Bir hata işleme yordamını etkinleştirir ve bir yordam içinde yordam konumunu belirtir. Ayrıca bir hata işleme yordamını devre dışı bırakmak için kullanılabilir.  
  
 Hata işleme olmadan, oluşan çalışma zamanı hataları önemli kabul: bir hata iletisi görüntülenir ve yürütmeyi durdurur.  
  
 Mümkün olduğunda, yapılandırılmamış özel durum işleme kullanmak yerine, kodunuzda işleme, yapılandırılmış özel durum kullanmanızı öneririz ve `On Error` deyimi. Daha fazla bilgi için [deneyin... Catch... Finally deyimini](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
> [!NOTE]
>  `Error` Anahtar sözcüğü kullanılan ayrıca [Error deyimi](../../../visual-basic/language-reference/statements/error-statement.md), geriye dönük uyumluluk için desteklenir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
On Error { GoTo [ line | 0 | -1 ] | Resume Next }  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`GoTo``line`|Gerekli belirtilen satırda başlatılan hata işleme yordamını etkinleştirir `line` bağımsız değişken. `line` Herhangi bir satır etiketi veya satır numarası bağımsız değişkendir. Bir çalışma zamanı hatası meydana gelirse, hata işleyicisi etkin hale getirme belirtilen satır dallara denetler. Belirtilen satır aynı yordam içinde olmalıdır `On Error` deyimi veya bir derleme zamanı hatası oluşur.|  
|`GoTo` 0|Etkin hata işleyiciyi güncel süreçte devre dışı bırakır ve kendisine sıfırlar `Nothing`.|  
|`GoTo` -1|Etkin istisnayı güncel süreçte devre dışı bırakır ve kendisine sıfırlar `Nothing`.|  
|`Resume Next`|Bir çalışma zamanı hatası oluştuğunda, Denetim burada bir hata oluştu ve bu noktadan sonra yürütülmesine devam deyimi hemen sonrasındaki deyime gider olduğunu belirtir. Bu formu kullanmak yerine `On Error GoTo` nesneleri erişirken.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Yapılandırılmamış özel durum işleme kullanmak yerine, mümkün olduğunda, kodunuzda yapılandırılmış özel durum işleme kullanmanızı öneririz ve `On Error` deyimi. Daha fazla bilgi için [deneyin... Catch... Finally deyimini](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
 Bir "etkin" hata işleyicisi tarafından açık bir yetenektir bir `On Error` deyimi. Bir hata işleme sürecinde olan etkin bir işleyici bir "etkin" hata işleyicidir.  
  
 Bir hata işleyicisi etkin olduğu sırada bir hata oluşursa (hata geçişi arasındaki ve `Resume`, `Exit Sub`, `Exit Function`, veya `Exit Property` deyimi), geçerli yordam hata işleyicisi hata işleyemiyor. Çağıran yordama denetimini döndürür.  
  
 Çağıran yordama bir etkin hata işleyiciyi varsa, hatayı işlemek için etkinleştirilir. Çağıran yordam hata işleyicisini de etkin değilse, denetim etkin, ancak etkin olmayan hata işleyicisi bulunana kadar önceki çağrı yordamlar geri geçer. Böyle bir hata işleyicisi bulunursa, aslında oluştuğu noktadan önemli bir hatadır.  
  
 Geri çağırma yordamı için denetimi hata işleyicisine aktarır her zaman güncel süreçte bu yordamı haline gelir. Herhangi bir yordamda bir hata işleyicisi tarafından bir hata işlenmiş sonra yürütme ile belirlenen bir noktada güncel süreçte sürdürür. `Resume` deyimi.  
  
> [!NOTE]
>  Bir hata işleme yordamını değil bir `Sub` yordamı veya `Function` yordamı. Satır etiketi veya bir satır numarası işaretlenmiş kod bölümüdür.  
  
## <a name="number-property"></a>Number özelliği  
 Hata işleme rutinleri değeri Bel `Number` özelliği `Err` hatanın nedenini belirlemek için nesne. Yordam test veya ilgili özellik değerlerini kaydetmek `Err` neden olabilecek bir yordamda daha önce bir hata çağrılır veya başka bir hata oluşabilir önce nesne. Özellik değerleri `Err` yansıtma yalnızca en son hata nesnesi. Hata iletisi ile ilişkili `Err.Number` bulunan `Err.Description`.  
  
## <a name="throw-statement"></a>Throw Deyimi  
 İle ortaya çıkan hata `Err.Raise` yöntemi kümeleri `Exception` özelliği yeni oluşturulan bir örneğine <xref:System.Exception> sınıfı. Türetilmiş bir özel durum türleri, özel durumlar yükseltme desteklemek için bir `Throw` dilde deyimi desteklenir. Bu, özel durum örneği harekete geçirilmesine tek bir parametre alır. Aşağıdaki örnek, bu özellikleri desteği var olan özel durum işleme ile nasıl kullanılacağını gösterir:  
  
 [!code-vb[VbVbalrErrorHandling#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#17)]  
  
 Dikkat `On Error GoTo` deyimi, özel durum sınıfı bağımsız olarak tüm hataları yakalar.  
  
## <a name="on-error-resume-next"></a>Hatada devam sonraki  
 `On Error Resume Next` hemen çalışma zamanı hatasına neden deyiminin sonrasındaki deyime ile devam etmek için veya yordam içeren dışında hemen en son sonrasındaki deyime ile çağrı yürütülmesine neden `On Error Resume Next` deyimi. Bu ifade, bir çalışma zamanı hatası rağmen devam etmek için yürütmeye izin verir. Yordam içinde başka bir konuma denetimi aktarma yerine hatanın nerede ortaya çıkabilecek hata işleme yordamını yerleştirebilirsiniz. Bir `On Error Resume Next` deyimi olur etkin olmayan başka bir yordam çağrıldığında, yürütülecek şekilde bir `On Error Resume Next` deyimi her işleme bu yordamı içinde satır içi hata istiyorsanız yordamı çağrılır.  
  
> [!NOTE]
>  `On Error Resume Next` Yapısı tercih `On Error GoTo` diğer nesnelere erişimi sırasında oluşturulan hataları işleme olduğunda. Denetimi `Err` bir nesne ile her etkileşim hakkında nesne kodu tarafından erişildi belirsizlik kaldırdıktan sonra. Hangi nesne hata kodunu yerleştirilen emin olabilirsiniz `Err.Number`, nesnenin ilk olarak hatayı oluşturan yanı sıra (belirtilen nesne `Err.Source`).  
  
## <a name="on-error-goto-0"></a>Error GoTo 0  
 `On Error GoTo 0` hata işleme güncel süreçte devre dışı bırakır. 0 numaralı bir satır yordamı içerse bile, satır 0 hata işleme kodu başlangıcı belirtmiyor. Olmadan bir `On Error GoTo 0` deyimi, bir hata işleyicisini otomatik olarak devre dışı olduğunda bir yordam çıkıldı.  
  
## <a name="on-error-goto--1"></a>-1 hata Git üzerinde  
 `On Error GoTo -1` özel durum güncel süreçte devre dışı bırakır. Yordamı -1 numaralı bir satır içeren olsa bile hata işleme kodu başlangıcı -1 satır belirtmiyor. Olmadan bir `On Error GoTo -1` deyimi, bir özel durum otomatik olarak devre dışı olduğunda bir yordam çıkıldı.  
  
 Hata işleme kodu hata oluşmadığında çalıştırmasını engellemek için yerleştirin bir `Exit Sub`, `Exit Function`, veya `Exit Property` deyiminden hemen önce aşağıdaki parçası olduğu gibi hata işleme yordamını:  
  
 [!code-vb[VbVbalrErrorHandling#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#18)]  
  
 Burada, aşağıdaki hata işleme kod `Exit Sub` deyimi ve önündeki `End Sub` yordamı akıştan ayırmak için deyimi. Bir yordamda hata işleme kodu herhangi bir yere yerleştirebilirsiniz.  
  
## <a name="untrapped-errors"></a>Untrapped hataları  
 Nesne, yürütülebilir bir dosya çalışırken nesneleri untrapped hatalarını denetleme uygulamaya döndürülür. Yalnızca uygun seçenekleri geliştirme ortamında untrapped hataları denetleme uygulamaya döndürülür. Hangi seçenekleri kümesi, hata ayıklama sırasında bunların nasıl ayarlanacağını ve konak sınıfları olup oluşturabilirsiniz olmalıdır bir açıklaması için konak uygulamanızın belgelerine bakın.  
  
 Diğer nesnelerin erişen bir nesne oluşturursanız, geri geçirmek işlenmemiş hataları işlemeye çalışmanız gerekir. Hata kodları eşlerseniz yükleyemezsiniz `Err.Number` hataları ve sonra geçişi birine nesnenizin çağırana geri. Hata kodunuza ekleyerek, hata belirtmelidir `VbObjectError` sabit. Hata kodunuzu 1052 ise, örneğin, gibi atayabilirsiniz:  
  
 [!code-vb[VbVbalrErrorHandling#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#19)]  
  
> [!CAUTION]
>  Windows dinamik bağlantı kitaplıklarını (DLL'ler) çağrı sırasında sistem hataları, özel durumlar harekete geçirmeyin ve Visual Basic hata yakalama ile yakalanan. DLL işlevleri çağırma, başarı veya başarısızlık (API belirtimlerini) göre her dönüş değerini denetlemeniz gerekir ve değeri bir hata olması durumunda iade `Err` nesnenin `LastDLLError` özelliği.  
  
## <a name="example"></a>Örnek  
 Bu örnekte ilk `On Error GoTo` deyimini bir yordam içinde bir hata işleme yordamını konumunu belirtin. Örnekte, hata numarası 6 sıfıra bölünme girişimi oluşturur. Hata hata işleme yordamınızda işlenir ve hataya neden deyimi sonra döndürülür. `On Error GoTo 0` Deyimi hata yakalama devre dışı bırakır. Ardından `On Error Resume Next` deyimi, böylece sonraki deyimi tarafından oluşturulan hata bağlamı belirli bilinmesi hata yakalama ertelemek için kullanılır. Unutmayın `Err.Clear` temizlemek için kullanılan `Err` hatanın işlenip sonra nesnenin özellikleri.  
  
 [!code-vb[VbVbalrErrorHandling#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#20)]  
  
## <a name="requirements"></a>Gereksinimler  
 **Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Derleme:** Visual Basic Çalışma Zamanı Kitaplığı (Microsoft.VisualBasic.dll içinde)  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Number%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Description%2A>
- <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>
- [End Deyimi](../../../visual-basic/language-reference/statements/end-statement.md)
- [Exit Deyimi](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Resume Deyimi](../../../visual-basic/language-reference/statements/resume-statement.md)
- [Hata İletileri](../../../visual-basic/language-reference/error-messages/index.md)
- [Try...Catch...Finally Deyimi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
