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
ms.openlocfilehash: 0297f7af29faf5a08472fd1d18ca52e9b2fda1af
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404414"
---
# <a name="on-error-statement-visual-basic"></a>On Error Deyimi (Visual Basic)
Bir hata işleme yordamını sunar ve yordamın içindeki konumunu belirtir; , hata işleme yordamını devre dışı bırakmak için de kullanılabilir. `On Error`İfade yapılandırılmamış hata işlemede kullanılır ve yapılandırılmış özel durum işleme yerine kullanılabilir. [Yapılandırılmış özel durum işleme](../../../standard/exceptions/index.md) .NET içinde yerleşiktir, genellikle daha etkilidir, bu nedenle uygulamanızda çalışma zamanı hatalarını işlerken önerilir.

 Hata işleme veya özel durum işleme olmadan, oluşan tüm çalışma zamanı hataları önemli: bir hata iletisi görüntülenir ve yürütme durdu.

> [!NOTE]
> `Error`Anahtar sözcüğü, geri uyumluluk için desteklenen [hata bildiriminde](error-statement.md)de kullanılır.

## <a name="syntax"></a>Sözdizimi

```vb
On Error { GoTo [ line | 0 | -1 ] | Resume Next }
```

## <a name="parts"></a>Bölümler

|Terim|Tanım|
|---|---|
|`GoTo` *line*|Gerekli *satır* bağımsız değişkeninde belirtilen satırda başlayan hata işleme yordamını sunar. *Satır* bağımsız değişkeni herhangi bir satır etiketi veya satır numarasıdır. Bir çalışma zamanı hatası oluşursa, dalları belirtilen satıra göre kontrol edin ve hata işleyicisini etkin hale getirir. Belirtilen satır, deyimle aynı yordamda `On Error` veya bir derleme zamanı hatasıyla oluşmalıdır.|
|`GoTo 0`|Etkin hata işleyicisini geçerli yordamda devre dışı bırakır ve öğesini olarak sıfırlar `Nothing` .|
|`GoTo -1`|Etkin özel durumu geçerli yordamda devre dışı bırakır ve öğesini olarak sıfırlar `Nothing` .|
|`Resume Next`|Bir çalışma zamanı hatası oluştuğunda, denetimin Hatanın gerçekleştiği deyimin hemen ardından ifadeye ve yürütmenin bu noktadan devam edeceğini belirtir. Nesnelere erişmek yerine bu formu kullanın `On Error GoTo` .|

## <a name="remarks"></a>Açıklamalar

> [!NOTE]
> Yapılandırılmamış özel durum işleme ve bildirisini kullanmak yerine kodunuzda yapılandırılmış özel durum işlemeyi kullanmanızı öneririz `On Error` . Daha fazla bilgi için bkz [. TRY... Yakala... Finally ekstresi](try-catch-finally-statement.md).

 Bir "etkin" hata işleyicisi bir deyime göre açılmış bir hatadır `On Error` . Bir "etkin" hata işleyicisi, bir hatayı işleme sürecinde olan etkin bir işleyicidir.

 Hata işleyicisi etkinken bir hata oluşursa (hata ve bir,, `Resume` `Exit Sub` `Exit Function` veya `Exit Property` bildiri arasında), geçerli yordamın hata işleyicisi hatayı işleyemez. Denetim, çağıran yordama döner.
  
 Çağıran yordamın etkin bir hata işleyicisi varsa, hatayı işlemek için etkinleştirilir. Çağıran yordamın hata işleyicisi de etkinse, etkin ancak etkin olmayan bir hata işleyicisi bulunana kadar, denetim önceki çağrı yordamlarıyla geri geçirilir. Böyle bir hata işleyicisi bulunmazsa, hata gerçekten gerçekleştiği noktada önemli olur.
  
 Hata işleyicisi denetimi bir çağrı yordamına geri geçirdiğinde, bu yordam geçerli yordam olur. Herhangi bir yordamda hata işleyicisi tarafından bir hata işlendikten sonra, yürütme geçerli yordamda deyimin tarafından belirlenen noktada devam eder `Resume` .
  
> [!NOTE]
> Hata işleme yordamı bir `Sub` yordam veya `Function` yordam değildir. Bir satır etiketi veya satır numarası tarafından işaretlenen kodun bir bölümüdür.
  
## <a name="number-property"></a>Number özelliği
 Hata işleme yordamları, `Number` `Err` hatanın nedenini öğrenmek için nesnesinin özelliğindeki değeri kullanır. Yordam, `Err` diğer herhangi bir hata gerçekleşebilmesi veya bir hataya neden olabilecek bir yordam çağrılmadan önce, nesne içindeki ilgili özellik değerlerini test etmelidir veya kaydeder. Nesnedeki özellik değerleri `Err` yalnızca en son hatayı yansıtır. İle ilişkili hata iletisi `Err.Number` içinde bulunur `Err.Description` .  
  
## <a name="throw-statement"></a>Throw Deyimi  
 Yöntemiyle oluşturulan bir hata, `Err.Raise` `Exception` özelliği, sınıfının yeni oluşturulmuş bir örneğine ayarlar <xref:System.Exception> . Türetilmiş özel durum türleri için özel durumların çıkarılmasını desteklemek amacıyla, `Throw` dilde bir ifade desteklenir. Bu, oluşturulacak özel durum örneği olan tek bir parametre alır. Aşağıdaki örnek, bu özelliklerin mevcut özel durum işleme desteğiyle nasıl kullanılabileceğini göstermektedir:

 [!code-vb[VbVbalrErrorHandling#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#17)]  
  
 `On Error GoTo`Deyimin, özel durum sınıfından bağımsız olarak tüm hataları yakaladığı konusunda dikkat edin.
  
## <a name="on-error-resume-next"></a>Hata durumunda devamında
 `On Error Resume Next`yürütmeye, çalışma zamanı hatasına neden olan deyimin hemen ardından gelen deyimle devam etmesine neden olur ya da deyimin bulunduğu yordamın en son çağrısından hemen sonra gelen deyimle devam eder `On Error Resume Next` . Bu ifade, yürütmenin çalışma zamanı hatasına rağmen devam etmesine izin verir. Hatanın gerçekleştiği hata işleme yordamını, yordamı yordamın içindeki başka bir konuma aktarmak yerine yerleştirebilirsiniz. `On Error Resume Next`Başka bir yordam çağrıldığında bir ifade devre dışı bırakılır, `On Error Resume Next` Bu nedenle bu yordamda satır içi hata işleme istiyorsanız, çağrılan her yordamda bir ifade yürütmelisiniz.
  
> [!NOTE]
> `On Error Resume Next` `On Error GoTo` Diğer nesnelere erişim sırasında oluşturulan hatalar işlenirken yapı tercih edilebilir. `Err`Bir nesneyle her bir etkileşime geçtikten sonra Denetim, kod tarafından hangi nesneye erişildiğine ilişkin belirsizliği ortadan kaldırır. Hangi nesnenin içinde hata kodu yerleştirdiğini `Err.Number` ve hangi nesnenin ilk olarak hatayı (içinde belirtilen nesne) üretdiğini de unutmayın `Err.Source` .

## <a name="on-error-goto-0"></a>Hatada git 0
 `On Error GoTo 0`geçerli yordamda hata işlemeyi devre dışı bırakır. Yordam 0 sayılı bir satır içerse bile, hata işleme kodunun başlangıcı olarak line 0 belirtmez. Bir `On Error GoTo 0` ifade olmadan, bir yordam çıkıldığında bir hata işleyicisi otomatik olarak devre dışı bırakılır.

## <a name="on-error-goto--1"></a>Hatada GoTo-1
 `On Error GoTo -1`geçerli yordamda özel durumu devre dışı bırakır. Yordam numaralandırılmış bir satır içerse de, hata işleme kodunun başlangıcı olarak Line-1 ' i belirtmez. Bir `On Error GoTo -1` ifade olmadan, bir yordama çıkıldığında bir özel durum otomatik olarak devre dışı bırakılır.

 Hata oluştuğunda hata işleme kodunun çalıştırılmasını engellemek için, `Exit Sub` `Exit Function` `Exit Property` aşağıdaki parçada olduğu gibi, hata işleme yordamının hemen öncesine bir, veya ifadesini yerleştirin:

 [!code-vb[VbVbalrErrorHandling#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#18)]

 Burada, hata işleme kodu `Exit Sub` ifadeyi izler ve `End Sub` yordam akışından ayırmak için deyimden önce gelir. Hata işleme kodunu bir yordamda herhangi bir yere yerleştirebilirsiniz.

## <a name="untrapped-errors"></a>Yakalangeri al hataları
 Nesneler yürütülebilir bir dosya olarak çalıştırıldığında denetim uygulamasına nesneler üzerinde yakalangeri dönüş hataları döndürülür. Geliştirme ortamında, yalnızca uygun seçenekler ayarlandıysa denetim uygulamasına geri dönüş hataları döndürülür. Hata ayıklama sırasında ayarlanması gereken seçeneklerin açıklaması, nasıl ayarlanacağı ve konağın sınıf oluşturup oluşturamayacağını gösteren bir açıklama için ana bilgisayar uygulamanızın belgelerine bakın.

 Diğer nesnelere erişen bir nesne oluşturursanız, geri aktardıkları işlenmemiş hataları işlemeye çalışırsınız. Bu durumda, içindeki hata kodlarını `Err.Number` kendi hatalardan biriyle eşleyin ve sonra bunları nesnenizin çağıranına geri geçirin. Hata kodunuzu sabite ekleyerek hatayı belirtmeniz gerekir `VbObjectError` . Örneğin, hata kodunuz 1052 ise, aşağıdaki gibi atayın:

 [!code-vb[VbVbalrErrorHandling#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#19)]

> [!CAUTION]
> Windows dinamik bağlantı kitaplıkları (dll 'Ler) çağrıları sırasında sistem hataları özel durum oluşturmaz ve Visual Basic hata yakalama ile yakalanamaz. DLL işlevlerini çağırırken, her dönüş değerini başarılı veya başarısız (API belirtimlerine göre) olarak denetlemeniz gerekir ve hata durumunda nesnenin özelliğindeki değeri kontrol edin `Err` `LastDLLError` .

## <a name="example"></a>Örnek
 Bu örnek öncelikle `On Error GoTo` bir yordam içindeki bir hata işleme yordamının konumunu belirtmek için ifadesini kullanır. Örnekte, sıfıra bölme girişimi 6 hata numarasını üretir. Hata, hata işleme yordamında işlenir ve denetim daha sonra hataya neden olan ifadeye döndürülür. `On Error GoTo 0`İfade hata yakalamayı kapatır. Daha sonra, `On Error Resume Next` Next ifadesinin oluşturduğu hatanın bağlamı belirli bir şekilde tanınabilmesi için hata yakalamayı erteleme için bu ifade kullanılır. `Err.Clear` `Err` Hata işlendikten sonra nesnenin özelliklerini temizlemek için kullanıldığını unutmayın.

 [!code-vb[VbVbalrErrorHandling#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#20)]

## <a name="requirements"></a>Gereksinimler
 **Ad alanı:** [Microsoft. VisualBasic](../runtime-library-members.md)

 **Bütünleştirilmiş kod:** Visual Basic çalışma zamanı kitaplığı (Microsoft. VisualBasic. dll içinde)

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Number%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Description%2A>
- <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>
- [End ekstresi](end-statement.md)
- [Exit Deyimi](exit-statement.md)
- [Resume Deyimi](resume-statement.md)
- [Hata İletileri](../error-messages/index.md)
- [Try...Catch...Finally Deyimi](try-catch-finally-statement.md)
