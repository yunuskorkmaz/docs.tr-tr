---
title: On Error Deyimi
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
ms.openlocfilehash: d62c2ba1849b7015ed877d503220026a2dfeff57
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353815"
---
# <a name="on-error-statement-visual-basic"></a>On Error Deyimi (Visual Basic)
Bir hata işleme yordamını sunar ve yordamın içindeki konumunu belirtir; , hata işleme yordamını devre dışı bırakmak için de kullanılabilir. `On Error` deyimleri yapılandırılmamış hata işlemede kullanılır ve yapılandırılmış özel durum işleme yerine kullanılabilir. [Yapılandırılmış özel durum işleme](../../../standard/exceptions/index.md) .NET içinde yerleşiktir, genellikle daha etkilidir, bu nedenle uygulamanızda çalışma zamanı hatalarını işlerken önerilir.

 Hata işleme veya özel durum işleme olmadan, oluşan tüm çalışma zamanı hataları önemli: bir hata iletisi görüntülenir ve yürütme durdu.

> [!NOTE]
> `Error` anahtar sözcüğü, geriye dönük uyumluluk için desteklenen [hata bildiriminde](../../../visual-basic/language-reference/statements/error-statement.md)de kullanılır.

## <a name="syntax"></a>Sözdizimi

```vb
On Error { GoTo [ line | 0 | -1 ] | Resume Next }
```

## <a name="parts"></a>Bölümler

|Terim|Tanım|
|---|---|
|`GoTo` *satırı*|Gerekli *satır* bağımsız değişkeninde belirtilen satırda başlayan hata işleme yordamını sunar. *Satır* bağımsız değişkeni herhangi bir satır etiketi veya satır numarasıdır. Bir çalışma zamanı hatası oluşursa, dalları belirtilen satıra göre kontrol edin ve hata işleyicisini etkin hale getirir. Belirtilen satırın `On Error` ifadesiyle aynı yordamda olması veya bir derleme zamanı hatası oluşması gerekir.|
|`GoTo 0`|Geçerli yordamda etkinleştirilmiş hata işleyicisini devre dışı bırakır ve `Nothing`için sıfırlar.|
|`GoTo -1`|Etkin özel durumu geçerli yordamda devre dışı bırakır ve `Nothing`olarak sıfırlar.|
|`Resume Next`|Bir çalışma zamanı hatası oluştuğunda, denetimin Hatanın gerçekleştiği deyimin hemen ardından ifadeye ve yürütmenin bu noktadan devam edeceğini belirtir. Nesnelere erişirken `On Error GoTo` yerine bu formu kullanın.|

## <a name="remarks"></a>Açıklamalar

> [!NOTE]
> Yapılandırılmamış özel durum işleme ve `On Error` deyimin kullanılması yerine kodunuzda yapılandırılmış özel durum işlemeyi kullanmanızı öneririz. Daha fazla bilgi için bkz [. TRY... Yakala... Finally ekstresi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).

 Bir "Enabled" hata işleyicisi, bir `On Error` ifadesiyle açık olan bir hatadır. Bir "etkin" hata işleyicisi, bir hatayı işleme sürecinde olan etkin bir işleyicidir.

 Hata işleyicisi etkinken bir hata oluşursa (hata ve bir `Resume`, `Exit Sub`, `Exit Function`veya `Exit Property` deyimiyle), geçerli yordamın hata işleyicisi hatayı işleyemez. Denetim, çağıran yordama döner.
  
 Çağıran yordamın etkin bir hata işleyicisi varsa, hatayı işlemek için etkinleştirilir. Çağıran yordamın hata işleyicisi de etkinse, etkin ancak etkin olmayan bir hata işleyicisi bulunana kadar, denetim önceki çağrı yordamlarıyla geri geçirilir. Böyle bir hata işleyicisi bulunmazsa, hata gerçekten gerçekleştiği noktada önemli olur.
  
 Hata işleyicisi denetimi bir çağrı yordamına geri geçirdiğinde, bu yordam geçerli yordam olur. Herhangi bir yordamda hata işleyicisi tarafından bir hata işlendikten sonra, yürütme geçerli yordamda `Resume` ifadesiyle belirlenen noktada devam eder.
  
> [!NOTE]
> Bir hata işleme yordamı `Sub` yordam veya `Function` yordamı değildir. Bir satır etiketi veya satır numarası tarafından işaretlenen kodun bir bölümüdür.
  
## <a name="number-property"></a>Number özelliği
 Hata işleme yordamları hatanın nedenini öğrenmek için `Err` nesnesinin `Number` özelliğindeki değeri kullanır. Yordam, diğer herhangi bir hatanın gerçekleşebilmesi veya bir hataya neden olabilecek bir yordam çağrılmadan önce `Err` nesnesinde ilgili özellik değerlerini test etmelidir veya kaydetmelidir. `Err` nesnesindeki özellik değerleri yalnızca en son hatayı yansıtır. `Err.Number` ilişkili hata iletisi `Err.Description`içinde yer alır.  
  
## <a name="throw-statement"></a>Throw Deyimi  
 `Err.Raise` yöntemiyle oluşturulan bir hata, `Exception` özelliğini <xref:System.Exception> sınıfının yeni oluşturulan örneğine ayarlar. Türetilmiş özel durum türleri için özel durumların çıkarılmasını desteklemek amacıyla, dilde bir `Throw` deyimleri desteklenir. Bu, oluşturulacak özel durum örneği olan tek bir parametre alır. Aşağıdaki örnek, bu özelliklerin mevcut özel durum işleme desteğiyle nasıl kullanılabileceğini göstermektedir:

 [!code-vb[VbVbalrErrorHandling#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#17)]  
  
 `On Error GoTo` ifadesinin, özel durum sınıfından bağımsız olarak tüm hataları yakaladığı konusunda dikkat edin.
  
## <a name="on-error-resume-next"></a>Hata durumunda devamında
 `On Error Resume Next` yürütme, çalışma zamanı hatasına neden olan deyimin hemen ardından gelen deyimle devam etmesine neden olur veya `On Error Resume Next` ifadesini içeren yordamın en son çağrısından hemen sonra gelen deyimle devam eder. Bu ifade, yürütmenin çalışma zamanı hatasına rağmen devam etmesine izin verir. Hatanın gerçekleştiği hata işleme yordamını, yordamı yordamın içindeki başka bir konuma aktarmak yerine yerleştirebilirsiniz. `On Error Resume Next` bir ifade başka bir yordam çağrıldığında devre dışı bırakılır, bu nedenle bu yordamda satır içi hata işleme istiyorsanız, çağrılan her yordamda bir `On Error Resume Next` ifadesini yürütmelisiniz.
  
> [!NOTE]
> `On Error Resume Next` yapısı, diğer nesnelere erişim sırasında oluşturulan hataları işlerken `On Error GoTo` tercih edilebilir. Bir nesne ile her bir etkileşime geçtikten sonra `Err` denetimi, kod tarafından hangi nesneye erişildiğine ilişkin belirsizliği ortadan kaldırır. Hangi nesnenin `Err.Number`hata kodunu yerleştirdiğini ve hangi nesnenin başlangıçta hata (`Err.Source`içinde belirtilen nesne) üretdiğini de sağlayabilirsiniz.

## <a name="on-error-goto-0"></a>Hatada git 0
 `On Error GoTo 0`, geçerli yordamda hata işlemeyi devre dışı bırakır. Yordam 0 sayılı bir satır içerse bile, hata işleme kodunun başlangıcı olarak line 0 belirtmez. Bir `On Error GoTo 0` deyimleri olmadan, bir yordam çıkıldığında bir hata işleyicisi otomatik olarak devre dışı bırakılır.

## <a name="on-error-goto--1"></a>Hatada GoTo-1
 `On Error GoTo -1`, geçerli yordamdaki özel durumu devre dışı bırakır. Yordam numaralandırılmış bir satır içerse de, hata işleme kodunun başlangıcı olarak Line-1 ' i belirtmez. Bir `On Error GoTo -1` deyimleri olmadan, bir yordama çıkıldığında bir özel durum otomatik olarak devre dışı bırakılır.

 Hata oluştuğunda hata işleme kodunun çalıştırılmasını engellemek için, aşağıdaki parçada olduğu gibi, hata işleme yordamının hemen önüne bir `Exit Sub`, `Exit Function`veya `Exit Property` ifadesini yerleştirin:

 [!code-vb[VbVbalrErrorHandling#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#18)]

 Burada, hata işleme kodu `Exit Sub` ifadesini izler ve yordam akışından ayırmak için `End Sub` deyimden önce gelir. Hata işleme kodunu bir yordamda herhangi bir yere yerleştirebilirsiniz.

## <a name="untrapped-errors"></a>Yakalangeri al hataları
 Nesneler yürütülebilir bir dosya olarak çalıştırıldığında denetim uygulamasına nesneler üzerinde yakalangeri dönüş hataları döndürülür. Geliştirme ortamında, yalnızca uygun seçenekler ayarlandıysa denetim uygulamasına geri dönüş hataları döndürülür. Hata ayıklama sırasında ayarlanması gereken seçeneklerin açıklaması, nasıl ayarlanacağı ve konağın sınıf oluşturup oluşturamayacağını gösteren bir açıklama için ana bilgisayar uygulamanızın belgelerine bakın.

 Diğer nesnelere erişen bir nesne oluşturursanız, geri aktardıkları işlenmemiş hataları işlemeye çalışırsınız. Bu durumda, `Err.Number` hata kodlarını kendi hatalardan biriyle eşleyin ve sonra bunları nesnenizin çağıranına geri geçirin. Hata kodunuzu `VbObjectError` sabitine ekleyerek hatayı belirtmeniz gerekir. Örneğin, hata kodunuz 1052 ise, aşağıdaki gibi atayın:

 [!code-vb[VbVbalrErrorHandling#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#19)]

> [!CAUTION]
> Windows dinamik bağlantı kitaplıkları (dll 'Ler) çağrıları sırasında sistem hataları özel durum oluşturmaz ve Visual Basic hata yakalama ile yakalanamaz. DLL işlevlerini çağırırken her bir dönüş değerini başarılı veya başarısız (API belirtimlerine göre) için denetlemeniz ve hata durumunda `Err` nesnesinin `LastDLLError` özelliğindeki değeri kontrol etmelisiniz.

## <a name="example"></a>Örnek
 Bu örnek öncelikle bir yordam içindeki bir hata işleme yordamının konumunu belirtmek için `On Error GoTo` ifadesini kullanır. Örnekte, sıfıra bölme girişimi 6 hata numarasını üretir. Hata, hata işleme yordamında işlenir ve denetim daha sonra hataya neden olan ifadeye döndürülür. `On Error GoTo 0` ifade, hata yakalamayı kapatır. Ardından, bir sonraki ifade tarafından oluşturulan hatanın bağlamı belirli bir şekilde bilinerek hata yakalamayı erteleme için `On Error Resume Next` ifade kullanılır. Hata işlendikten sonra `Err` nesnenin özelliklerini temizlemek için `Err.Clear` kullanıldığını unutmayın.

 [!code-vb[VbVbalrErrorHandling#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#20)]

## <a name="requirements"></a>Gereksinimler
 **Ad alanı:** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)

 **Bütünleştirilmiş kod:** Visual Basic çalışma zamanı kitaplığı (Microsoft. VisualBasic. dll içinde)

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
