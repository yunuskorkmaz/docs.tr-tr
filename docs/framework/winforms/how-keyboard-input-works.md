---
title: Klavye Girdisi Nasıl Çalışır
ms.date: 03/30/2017
helpviewer_keywords:
- keyboard input [Windows Forms], about keyboard input
- keyboards [Windows Forms], keyboard input
- Windows Forms, keyboard input
ms.assetid: 9a29433c-a180-49bb-b74c-d187786584c8
ms.openlocfilehash: ddc2f3338b231ab3ae59e65bc82c00bb8f663540
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61966978"
---
# <a name="how-keyboard-input-works"></a>Klavye Girdisi Nasıl Çalışır
Windows Forms klavye girdisi Windows iletilere yanıt olarak klavye olayları yükselterek işler. Çoğu Windows Forms uygulamaları klavye girişi, klavye olaylarını işleme tarafından özel olarak işler. Ancak, bir denetim ulaşmadan önce anahtarları kesintiye gibi daha gelişmiş klavye girişi senaryoları uygulayabilmesi klavye iletileri nasıl çalıştığını anlamak gerekir. Bu konu, Windows Forms tanır ve klavye iletileri nasıl yönlendirileceğini genel bir bakış sağlar anahtar veri türlerini açıklar. Klavye olaylarını hakkında daha fazla bilgi için bkz. [kullanan klavye olayları](using-keyboard-events.md).  
  
## <a name="types-of-keys"></a>Anahtar türü  
 Windows Forms bit düzeyi tarafından temsil edilen sanal anahtar kodlarını olarak klavye girişi tanımlayan <xref:System.Windows.Forms.Keys> sabit listesi. İle <xref:System.Windows.Forms.Keys> numaralandırma basılı tuşlarını kullanarak tek bir değer bir dizi birleştirebilirsiniz. Bu değerler WM_KEYDOWN ve WM_SYSKEYDOWN Windows iletilerle değerlere karşılık gelir. Çoğu fiziksel tuş basışlarını işleyerek algılayabilir <xref:System.Windows.Forms.Control.KeyDown> veya <xref:System.Windows.Forms.Control.KeyUp> olayları. Karakter anahtarları olan bir alt kümesini <xref:System.Windows.Forms.Keys> numaralandırma ve WM_CHAR ve WM_SYSCHAR Windows iletilerle değerlere karşılık gelir. Basılan anahtarları birleşimi bir karakter sonuçlanırsa, karakter işleyerek algılayabilir <xref:System.Windows.Forms.Control.KeyPress> olay. Alternatif olarak, <xref:Microsoft.VisualBasic.Devices.Keyboard>, hangi anahtarları basılan bulmak ve anahtarları göndermek için Visual Basic programlama arabirimi tarafından sunulan. Daha fazla bilgi için [klavyeye erişme](~/docs/visual-basic/developing-apps/programming/computer-resources/accessing-the-keyboard.md).  
  
## <a name="order-of-keyboard-events"></a>Klavye olayların sırası  
 Daha önce belirtildiği gibi var olan 3 klavye ile denetim oluşabilecek ilgili olaylar. Genel olayların sırası aşağıdaki sırayı gösterir:  
  
1. Kullanıcı, "a" anahtarı gönderir, bu anahtar, gönderilen, önceden işlenmiş ve bir <xref:System.Windows.Forms.Control.KeyDown> olayı oluşur.  
  
2. Kullanıcı, "a" anahtar tutar, bu anahtar, gönderilen, önceden işlenmiş ve bir <xref:System.Windows.Forms.Control.KeyPress> olayı oluşur.  
  
     Bu olay, kullanıcı tutan bir anahtar olarak birden çok kez gerçekleşir.  
  
3. "A" anahtar, anahtar önceden işlenmiş, kullanıcı yayınlar gönderilir ve <xref:System.Windows.Forms.Control.KeyUp> olayı oluşur.  
  
## <a name="preprocessing-keys"></a>Ön işleme anahtarları  
 Klavye iletileri işlenir diğer iletiler gibi <xref:System.Windows.Forms.Control.WndProc%2A> bir form veya denetim yöntemi. Bununla birlikte, önce klavye iletileri işlenir, <xref:System.Windows.Forms.Control.PreProcessMessage%2A> yöntemi özel karakter anahtarlar ve fiziksel anahtarlar işlemek için geçersiz kılınabilir bir veya daha fazla yöntemi çağırır. Algılama ve iletileri denetim tarafından işlenmeden önce belirli anahtarlar filtrelemek için bu yöntemleri geçersiz kılabilirsiniz. Aşağıdaki tabloda, yöntemi oluştuğunu sırada gerçekleştirilmekte olan eylemin ve ortaya çıkan, ilgili bir yöntemi gösterir.  
  
### <a name="preprocessing-for-a-keydown-event"></a>KeyDown olayı için ön işleme  
  
|Eylem|İlgili yöntemi|Notlar|  
|------------|--------------------|-----------|  
|Hızlandırıcı veya kısayol menüsü gibi bir komut anahtarı kontrol edin.|<xref:System.Windows.Forms.Control.ProcessCmdKey%2A>|Bu yöntem, normal anahtarların üzerine öncelikli bir komut anahtarı işler. Bu yöntem döndürürse `true`, anahtar ileti değil gönderilir ve önemli bir olay meydana gelmez. Döndürürse `false`, <xref:System.Windows.Forms.Control.IsInputKey%2A> çağrılır`.`|  
|Denetleme ön işleme gerektiren özel bir anahtar veya tetiklemelidir bir normal karakter anahtarı için bir <xref:System.Windows.Forms.Control.KeyDown> olay ve denetim için dağıtılması.|<xref:System.Windows.Forms.Control.IsInputKey%2A>|Yöntem döndürüyorsa `true`, Denetim olan normal bir karakter anlamına gelir ve <xref:System.Windows.Forms.Control.KeyDown> olayı oluşturulur. Varsa `false`, <xref:System.Windows.Forms.Control.ProcessDialogKey%2A> çağrılır. **Not:**  Bir denetimi alır bir anahtar veya anahtarlarının emin olmak için işleyebileceği <xref:System.Windows.Forms.Control.PreviewKeyDown> olay ve kümesi <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A> , <xref:System.Windows.Forms.PreviewKeyDownEventArgs> için `true` anahtar veya anahtarlarının istediğiniz.|  
|Gezinti için bir anahtar (ESC, sekme, dönüş veya ok tuşları) denetleyin.|<xref:System.Windows.Forms.Control.ProcessDialogKey%2A>|Bu yöntem denetiminde odak denetim ile üst arasında geçiş yapma gibi özel işlevler kullanan bir fiziksel anahtar işler. Kontrol anahtar işlemez <xref:System.Windows.Forms.Control.ProcessDialogKey%2A> üst denetime vb. hiyerarşideki en üst denetim üzerinde çağrılır. Bu yöntem döndürürse `true`, ön işleme tamamlandıktan ve anahtar olay oluşturulmuyor. Döndürürse `false`, <xref:System.Windows.Forms.Control.KeyDown> olayı oluşur.|  
  
### <a name="preprocessing-for-a-keypress-event"></a>KeyPress olayı için ön işleme  
  
|Eylem|İlgili yöntemi|Notlar|  
|------------|--------------------|-----------|  
|Anahtar denetim tarafından işlenmesi gerektiğini normal bir karakter olup olmadığını denetleyin|<xref:System.Windows.Forms.Control.IsInputChar%2A>|Bu yöntem karakter normal bir karakter olup olmadığını döndürür `true`, <xref:System.Windows.Forms.Control.KeyPress> olayı tetiklenir ve başka ön işleme gerçekleşir. Aksi takdirde <xref:System.Windows.Forms.Control.ProcessDialogChar%2A> olarak adlandırılır.|  
|Karakteri bir anımsatıcı (gibi & Tamam düğmesi üzerinde) olup olmadığını denetleyin|<xref:System.Windows.Forms.Control.ProcessDialogChar%2A>|Bu yöntem, benzer <xref:System.Windows.Forms.Control.ProcessDialogKey%2A>, denetim hiyerarşisi olarak adlandırılır. Denetim bir kapsayıcı denetimi ise çağırarak anımsatıcıları için denetler <xref:System.Windows.Forms.Control.ProcessMnemonic%2A> kendisi ve onun alt denetimler. Varsa <xref:System.Windows.Forms.Control.ProcessDialogChar%2A> döndürür `true`, <xref:System.Windows.Forms.Control.KeyPress> olay oluşmaz.|  
  
## <a name="processing-keyboard-messages"></a>Klavye iletilerini işleme  
 Klavye iletileri ulaşma sonra <xref:System.Windows.Forms.Control.WndProc%2A> yöntemi bir form veya denetim bir dizi geçersiz kılınabilir yöntemleri tarafından işlenir. Bu yöntemlerin her biri döndürür bir <xref:System.Boolean> klavye ileti işlendikten ve denetim tarafından kullanılan olup olmadığını belirten değeri. Yöntemlerden birini döndürürse `true`ileti işlenen değerlendirilir ve bu denetimin taban veya üst daha ayrıntılı işleme için geçirilir. Aksi takdirde, iletinin ileti kuyruğunda kalır ve denetimin temel ya da üst başka bir yöntem olarak işlenebilir. Klavye iletileri işleyen yöntemler aşağıdaki tabloda sunulmaktadır.  
  
|Yöntem|Notlar|  
|------------|-----------|  
|<xref:System.Windows.Forms.Control.ProcessKeyMessage%2A>|Bu yöntem tarafından alınan tüm klavye iletileri işleyen <xref:System.Windows.Forms.Control.WndProc%2A> denetimin yöntemi.|  
|<xref:System.Windows.Forms.Control.ProcessKeyPreview%2A>|Bu yöntem, üst denetimin klavye iletisi gönderir. Varsa <xref:System.Windows.Forms.Control.ProcessKeyPreview%2A> döndürür `true`, anahtar olay, aksi takdirde oluşturulan <xref:System.Windows.Forms.Control.ProcessKeyEventArgs%2A> çağrılır.|  
|<xref:System.Windows.Forms.Control.ProcessKeyEventArgs%2A>|Bu yöntem başlatır <xref:System.Windows.Forms.Control.KeyDown>, <xref:System.Windows.Forms.Control.KeyPress>, ve <xref:System.Windows.Forms.Control.KeyUp> olayları, uygun şekilde.|  
  
## <a name="overriding-keyboard-methods"></a>Klavye yöntemleri geçersiz kılma  
 Bir klavye iletisi önceden işlenmiş ve işlendiği zaman geçersiz kılmak için kullanılabilir birçok yöntem vardır; Ancak, bazı yöntemler diğerlerinden çok daha iyi seçenek değildir. Aşağıdaki tablo, görevleri gerçekleştirmek isteyebileceğiniz ve klavye yöntemleri geçersiz kılmak için en iyi yolu gösterir. Geçersiz kılma yöntemleri ile ilgili daha fazla bilgi için bkz: [özellikleri ve yöntemleri geçersiz kılan türetilmiş sınıfları](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md#overriding-properties-and-methods-in-derived-classes).  
  
|Görev|Yöntem|  
|----------|------------|  
|Bir gezinti anahtar kesebilir ve yükseltmek bir <xref:System.Windows.Forms.Control.KeyDown> olay. Örneğin sekme ve dönüş metin kutusunda işlenecek isteyebilirsiniz.|Geçersiz kılma <xref:System.Windows.Forms.Control.IsInputKey%2A>. **Not:**  Alternatif olarak, işleyebileceği <xref:System.Windows.Forms.Control.PreviewKeyDown> olay ve kümesi <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A> , <xref:System.Windows.Forms.PreviewKeyDownEventArgs> için `true` anahtar veya anahtarlarının istediğiniz.|  
|Özel giriş veya gezinti işleme bir denetim üzerinde gerçekleştirin. Örneğin, seçili öğeyi değiştirmek için liste denetimi ok tuşlarını kullanımını isteyebilirsiniz.|geçersiz kılma <xref:System.Windows.Forms.Control.ProcessDialogKey%2A>|  
|Bir gezinti anahtar kesebilir ve yükseltmek bir <xref:System.Windows.Forms.Control.KeyPress> olay. Örneğin bir döndürme kutusu denetiminde öğeleri aracılığıyla ilerlemeyi hızlandırmak için birden çok ok tuşuna bastığında isteyebilirsiniz.|Geçersiz kılma <xref:System.Windows.Forms.Control.IsInputChar%2A>.|  
|Özel giriş veya gezinti işleme sırasında gerçekleştirmek bir <xref:System.Windows.Forms.Control.KeyPress> olay. Örneğin, bir listede r harfi ile başlayan öğeleri arasında "r" tuşunu basılı tutarak denetimi atlar.|geçersiz kılma <xref:System.Windows.Forms.Control.ProcessDialogChar%2A>|  
|Özel anımsatıcı işlemeyi gerçekleştirir; Örneğin, araç çubuğunda yer alan özelleştirilmiş olarak çizilen düğme üzerinde anımsatıcıları işlemek istersiniz.|Geçersiz kılma <xref:System.Windows.Forms.Control.ProcessMnemonic%2A>.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Keys>
- <xref:System.Windows.Forms.Control.WndProc%2A>
- <xref:System.Windows.Forms.Control.PreProcessMessage%2A>
- [My.Computer.Keyboard Nesnesi](~/docs/visual-basic/language-reference/objects/my-computer-keyboard-object.md)
- [Klavyeye Erişme](~/docs/visual-basic/developing-apps/programming/computer-resources/accessing-the-keyboard.md)
- [Klavye Olaylarını Kullanma](using-keyboard-events.md)
