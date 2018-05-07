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
ms.openlocfilehash: b2e32dcca2e29a178af6dc985da536b47f0ebae6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="on-error-statement-visual-basic"></a>On Error Deyimi (Visual Basic)
Hata işleme yordamını etkinleştirir ve yordam bir yordam içindeki konumunu belirtir; Ayrıca bir hata işleme yordamı devre dışı bırakmak için kullanılabilir.  
  
 Hata işleme olmadan oluşan herhangi bir çalışma zamanı hata önemli: bir hata iletisi görüntülenir ve çalışmayı durdurur.  
  
 Mümkün olduğunda, yapılandırılmamış özel durum işleme kullanmak yerine, kodunuzda işleme yapılandırılmış özel durum kullandığınız önermek ve `On Error` deyimi. Daha fazla bilgi için bkz: [deneyin... Catch... Finally ifadesi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
> [!NOTE]
>  `Error` Anahtar sözcüğü kullanılan de [hata bildirimi](../../../visual-basic/language-reference/statements/error-statement.md), geriye dönük uyumluluk için desteklenir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
On Error { GoTo [ line | 0 | -1 ] | Resume Next }  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`GoTo``line`|Gerekli içinde belirtilen satır başlar hata işleme yordamını etkinleştirir `line` bağımsız değişkeni. `line` Bağımsız değişkeni olan herhangi bir satır etiket veya satır numarası. Bir çalışma zamanı hatası meydana gelirse, hata işleyicisine etkin hale getirme belirtilen satır dalları denetler. Belirtilen satır yordamın aynısını olmalıdır `On Error` deyimi veya bir derleme zamanı hatası oluşur.|  
|`GoTo` 0|Etkin hata işleyicisi geçerli yordamdaki devre dışı bırakır ve kendisine sıfırlar `Nothing`.|  
|`GoTo` -1|Geçerli yordamdaki etkin özel durumu devre dışı bırakır ve kendisine sıfırlar `Nothing`.|  
|`Resume Next`|Bir çalışma zamanı hatası meydana geldiğinde denetim hemen burada bir hata oluştu ve bu noktadan itibaren yürütülmeye deyiminden deyimi gider olduğunu belirtir. Bu biçimi kullanmak yerine `On Error GoTo` nesneleri erişirken.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Yapılandırılmamış özel durum işleme kullanmak yerine, mümkün olduğunda, kodunuzda yapılandırılmış özel durum işleme kullanmanızı öneririz ve `On Error` deyimi. Daha fazla bilgi için bkz: [deneyin... Catch... Finally ifadesi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
 Bir "enabled" hata işleyici tarafından açık biridir bir `On Error` deyimi. Hata işleme sürecinde olduğundan etkin bir işleyici bir "active" hata işleyicidir.  
  
 Bir hata işleyicisi etkin olduğu sırada bir hata oluşursa (hata arasındaki ve `Resume`, `Exit Sub`, `Exit Function`, veya `Exit Property` deyimi), geçerli yordam hata işleyicisine hata işleyemiyor. GetTypeId yordamını denetimini döndürür.  
  
 GetTypeId yordamını etkin hata işleyicisine varsa, hatayı işlemek için etkinleştirilir. Arama yordam hata işleyicisine ayrıca etkin değilse, etkin, ancak etkin olmayan hata işleyicisine bulunana kadar denetim geri önceki arama yordamları geçirir. Bu tür bir hata işleyicisine bulunursa, aslında oluştuğu noktadan önemli bir hatadır.  
  
 Geri arama yordamı için denetimi hata işleyicisine geçirir her zaman geçerli yordamın bu yordamı haline gelir. Hata herhangi bir yordam içinde bir hata işleyicisi tarafından işlenir sonra belirlenen noktada geçerli yordamdaki yürütme sürdürür `Resume` deyimi.  
  
> [!NOTE]
>  Hata işleme yordamı değil bir `Sub` yordamı veya `Function` yordamı. Kod bir satır etiketi veya bir satır sayısı işaretlenmiş bir bölümdür.  
  
## <a name="number-property"></a>Number özelliği  
 Hata işleme yordamları değeri Bel `Number` özelliği `Err` hatanın nedenini belirlemek için nesne. Yordamı test veya ilgili özellik değerlerini kaydetmek `Err` neden olabilecek bir yordamda daha önce bir hata olarak adlandırılan veya başka bir hata oluşabilir önce nesne. Özellik değerleri `Err` yalnızca en son hata yansıtma nesnesi. Hata iletisi ile ilişkili `Err.Number` bulunan `Err.Description`.  
  
## <a name="throw-statement"></a>Throw Deyimi  
 İle gerçekleştirilen bir hata `Err.Raise` yöntemi kümeleri `Exception` yeni oluşturulan bir örneğine özelliği <xref:System.Exception> sınıfı. Türetilen özel durum türleri, özel durumlar yükseltme desteklemek için bir `Throw` deyimi dilde desteklenir. Bu durum için özel durum örneğidir tek bir parametre alır. Aşağıdaki örnek, bu özellikler destek var olan özel durum işleme ile nasıl kullanılacağını gösterir:  
  
 [!code-vb[VbVbalrErrorHandling#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_1.vb)]  
  
 Dikkat `On Error GoTo` deyimi özel durum sınıfı bağımsız olarak tüm hataları yakalar.  
  
## <a name="on-error-resume-next"></a>Hatada devam sonraki  
 `On Error Resume Next` hemen çalıştırma hatası nedeniyle deyimi aşağıdaki deyim ile devam etmek veya dışında içeren yordamı hemen en son aşağıdaki deyimiyle arama yürütme neden `On Error Resume Next` deyimi. Bu deyim bir çalışma zamanı hatası rağmen devam etmek yürütme sağlar. Yordam içinde başka bir konuma denetim aktarma yerine burada hata ortaya çıkabilecek hata işleme yordamı yerleştirebilirsiniz. Bir `On Error Resume Next` deyimi hale etkin olmayan başka bir yordam çağrıldığında, yürütülecek şekilde bir `On Error Resume Next` deyimi her satır içi hata içinde yordamında işleme istiyorsanız, yordamı çağrılır.  
  
> [!NOTE]
>  `On Error Resume Next` Yapı için tercih `On Error GoTo` diğer nesnelere erişimi sırasında oluşturulan hatalar işlerken. Denetimi `Err` her bir nesne etkileşim hakkında nesne erişilen kodla belirsizlik kaldırdıktan sonra. Hangi nesne hata kodunu yerleştirilen emin olabilirsiniz `Err.Number`, hangi nesne başlangıçta hatayı oluşturan yanı sıra (belirtilen nesne `Err.Source`).  
  
## <a name="on-error-goto-0"></a>Error GoTo 0  
 `On Error GoTo 0` hata işleme geçerli yordamda devre dışı bırakır. 0 numaralı bir satır yordamı içerse bile, satır 0 hata işleme kodu başlangıç belirtmiyor. Olmadan bir `On Error GoTo 0` deyimi, bir hata işleyicisi otomatik olarak devre dışı bir yordam çıkıldı olduğunda.  
  
## <a name="on-error-goto--1"></a>Error GoTo -1  
 `On Error GoTo -1` Geçerli yordamdaki özel durumu devre dışı bırakır. Yordam -1 numaralı satırda varsa bile hata işleme kodu başlangıç -1 satır belirtmiyor. Olmadan bir `On Error GoTo -1` deyimi, bir özel durum otomatik olarak devre dışı olduğunda bir yordam çıkıldı.  
  
 Hata işleme kodu herhangi bir hata oluştuğunda çalıştırmasını engellemek için yerleştirin bir `Exit Sub`, `Exit Function`, veya `Exit Property` deyimi aşağıdaki parçası olduğu gibi hata işleme yordamı hemen önce:  
  
 [!code-vb[VbVbalrErrorHandling#18](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_2.vb)]  
  
 Burada, hata işleme kodu izleyen `Exit Sub` deyimi ve önündeki `End Sub` yordamı akışından ayırmak için deyimi. Hata işleme kodu bir yordamda herhangi bir yere yerleştirebilirsiniz.  
  
## <a name="untrapped-errors"></a>Untrapped hataları  
 Nesne yürütülebilir bir dosya çalıştırırken nesneleri untrapped hataları kontrol eden uygulamaya döndürülür. Yalnızca uygun seçenekleri geliştirme ortamında untrapped hataları kontrol eden uygulamaya döndürülür. Hata ayıklama sırasında kümesi, bunları nasıl ayarlayacağınız ve ana bilgisayar sınıfları olup oluşturabilirsiniz hangisinin seçenekleri olmalıdır açıklaması konak uygulamanızın belgelerine bakın.  
  
 Diğer nesneler erişen bir nesne oluşturursanız, geri geçirirler işlenmemiş hataları işlemek denemelisiniz. Hata kodları eşlerseniz yükleyemezsiniz `Err.Number` birine kendi hataları ve sonra geçişi nesnenizin çağırana yedekleyin. Hata kodunuza ekleyerek, hata belirtmelisiniz `VbObjectError` sabit. Hata kodu 1052 ise, örneğin, aşağıdaki gibi atayın:  
  
 [!code-vb[VbVbalrErrorHandling#19](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_3.vb)]  
  
> [!CAUTION]
>  Sistem hataları Windows dinamik bağlantı kitaplıklarını (DLL'ler) çağrı sırasında özel durumlar yükseltmeyin ve Visual Basic hata yakalama ile yakalanan. DLL işlevleri çağırma olduğunda başarı veya başarısızlık (API belirtimlerine uygun), her dönüş değerini denetleyin ve bir arıza olması durumunda değeri iade `Err` nesnenin `LastDLLError` özelliği.  
  
## <a name="example"></a>Örnek  
 Bu örnekte ilk `On Error GoTo` deyimi bir yordam içinde bir hata işleme yordamı konumunu belirtin. Örnekte, hata numarası 6 sıfıra bölünme girişimi oluşturur. Hata hata işleme yordamında işlenir ve hataya neden deyim sonra döndürülür. `On Error GoTo 0` Deyimi hata yakalama devre dışı bırakır. Ardından `On Error Resume Next` deyimi next deyimi tarafından oluşturulan hata bağlamının belirli bilinmesi böylece hata yakalama ertelemek için kullanılır. Unutmayın `Err.Clear` temizlemek için kullanılan `Err` hatası işlenir sonra nesnenin özellikleri.  
  
 [!code-vb[VbVbalrErrorHandling#20](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_4.vb)]  
  
## <a name="requirements"></a>Gereksinimler  
 **Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Derleme:** Visual Basic çalışma zamanı kitaplığı (Microsoft.VisualBasic.dll içinde)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.Information.Err%2A>  
 <xref:Microsoft.VisualBasic.ErrObject.Number%2A>  
 <xref:Microsoft.VisualBasic.ErrObject.Description%2A>  
 <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>  
 [End Deyimi](../../../visual-basic/language-reference/statements/end-statement.md)  
 [Exit Deyimi](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [Resume Deyimi](../../../visual-basic/language-reference/statements/resume-statement.md)  
 [Hata İletileri](../../../visual-basic/language-reference/error-messages/index.md)  
 [Try...Catch...Finally Deyimi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
