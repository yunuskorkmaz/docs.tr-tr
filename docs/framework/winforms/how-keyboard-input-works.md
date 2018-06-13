---
title: Klavye Girdisi Nasıl Çalışır
ms.date: 03/30/2017
helpviewer_keywords:
- keyboard input [Windows Forms], about keyboard input
- keyboards [Windows Forms], keyboard input
- Windows Forms, keyboard input
ms.assetid: 9a29433c-a180-49bb-b74c-d187786584c8
ms.openlocfilehash: a0b814a18f4a8b25fba9fa0b36da44954590f056
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541352"
---
# <a name="how-keyboard-input-works"></a>Klavye Girdisi Nasıl Çalışır
Windows Forms klavye olayları Windows iletilere yanıt olarak yükselterek klavye girişi işler. Çoğu Windows Forms uygulamaları klavye olayları işleme tarafından özel olarak klavye girişi işleyin. Ancak, bir denetim düşmeden önce anahtarları kesintiye uğratan gibi daha gelişmiş klavye girişi senaryolar uygulayabilirsiniz şekilde klavye iletileri nasıl çalıştığını anlamanız gerekir. Bu konuda Windows Forms tanır ve klavye iletileri nasıl yönlendirildiği genel bir bakış sağlar anahtar veri türleri açıklanmaktadır. Klavye olayları hakkında daha fazla bilgi için bkz: [kullanan klavye olayları](../../../docs/framework/winforms/using-keyboard-events.md).  
  
## <a name="types-of-keys"></a>Anahtarları türleri  
 Windows Forms Bitsel tarafından temsil edilen sanal anahtarı kodlar olarak klavye girişi tanımlayan <xref:System.Windows.Forms.Keys> numaralandırması. İle <xref:System.Windows.Forms.Keys> numaralandırma, tek bir değer neden basılı anahtarları bir dizi birleştirebilirsiniz. Bu değerler WM_KEYDOWN ve WM_SYSKEYDOWN Windows iletilerle değerlere karşılık gelir. Çoğu fiziksel anahtar basarsa işleyerek algılayabilir <xref:System.Windows.Forms.Control.KeyDown> veya <xref:System.Windows.Forms.Control.KeyUp> olaylar. Karakter tuşları olan bir alt kümesini <xref:System.Windows.Forms.Keys> numaralandırma ve WM_CHAR ve WM_SYSCHAR Windows iletilerle değerlere karşılık gelir. Basılı anahtarları birleşimi bir karakter sonuçlanırsa karakter işleyerek algılayabilir <xref:System.Windows.Forms.Control.KeyPress> olay. Alternatif olarak, kullanabileceğiniz <xref:Microsoft.VisualBasic.Devices.Keyboard>, hangi anahtarları basılmış bulmak ve anahtarlarını göndermek için Visual Basic programlama arabirimini tarafından sunulan. Daha fazla bilgi için bkz: [klavyeye erişme](~/docs/visual-basic/developing-apps/programming/computer-resources/accessing-the-keyboard.md).  
  
## <a name="order-of-keyboard-events"></a>Klavye olayların sırası  
 Daha önce listelenen gibi mevcuttur 3 klavye denetim oluşabilir ilgili olaylar. Aşağıdaki olaylar genel sırasını gösterilir:  
  
1.  Kullanıcı "a" anahtar iter, anahtar, dağıtılan, ön işlemesi yapılan ve bir <xref:System.Windows.Forms.Control.KeyDown> olayı oluşur.  
  
2.  Kullanıcı "a" anahtar tutar, bu anahtar, dağıtılan, ön işlemesi yapılan ve bir <xref:System.Windows.Forms.Control.KeyPress> olayı oluşur.  
  
     Kullanıcı bir anahtarı tutan gibi bu olayın birden çok kez gerçekleşir.  
  
3.  "A" anahtar, anahtar ön işlemesi yapılan, kullanıcı sürümleri gönderilir ve <xref:System.Windows.Forms.Control.KeyUp> olayı oluşur.  
  
## <a name="preprocessing-keys"></a>Anahtarları ön işleme  
 Klavye iletileri işlenir diğer iletileri gibi <xref:System.Windows.Forms.Control.WndProc%2A> bir form veya denetim yöntemi. Ancak, önce klavye iletileri işlenir, <xref:System.Windows.Forms.Control.PreProcessMessage%2A> yöntemi özel karakter anahtarları ve fiziksel anahtarları işlemek için geçersiz bir veya daha fazla yöntemi çağırır. Algılamak ve iletileri denetim tarafından işlenmeden önce belirli anahtarları filtrelemek için bu yöntemleri geçersiz kılabilirsiniz. Aşağıdaki tabloda yöntemi oluştuğunu sırayla gerçekleştirilen eylem ve oluşur, ilgili bir yöntemi gösterir.  
  
### <a name="preprocessing-for-a-keydown-event"></a>KeyDown olayı için ön işleme  
  
|Eylem|İlgili yöntemi|Notlar|  
|------------|--------------------|-----------|  
|Hızlandırıcı veya menü kısayolu gibi bir komut anahtarı olup olmadığını denetleyin.|<xref:System.Windows.Forms.Control.ProcessCmdKey%2A>|Bu yöntem normal anahtarlar üzerinden önceliklidir bir komut anahtarı işler. Bu yöntem döndürürse `true`, anahtar ileti değil gönderilir ve anahtar olayı oluşmaz. Döndürürse `false`, <xref:System.Windows.Forms.Control.IsInputKey%2A> çağrılır`.`|  
|Ön işleme gerektiren özel bir anahtar veya tetiklemelidir normal karakter anahtarı olup olmadığını denetleyin bir <xref:System.Windows.Forms.Control.KeyDown> olay ve bir denetim için gönderilir.|<xref:System.Windows.Forms.Control.IsInputKey%2A>|Yöntem döndürüyorsa `true`, denetimidir normal karakter anlamına gelir ve bir <xref:System.Windows.Forms.Control.KeyDown> olayı oluşturulur. Varsa `false`, <xref:System.Windows.Forms.Control.ProcessDialogKey%2A> olarak adlandırılır. **Not:** denetim alır bir anahtar ya da anahtarları birleşimi emin olmak için işleyebilir <xref:System.Windows.Forms.Control.PreviewKeyDown> olay ve kümesi <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A> , <xref:System.Windows.Forms.PreviewKeyDownEventArgs> için `true` anahtarı veya istediğiniz anahtarları için.|  
|Gezinti için bir anahtar (ESC, sekme, dönüş veya ok tuşları) denetleyin.|<xref:System.Windows.Forms.Control.ProcessDialogKey%2A>|Bu yöntem odak denetim ile üst arasında geçiş yapma gibi denetimi içinde özel işlevselliği kullanan bir fiziksel anahtar işler. Hemen denetim anahtarı işlemiyor varsa <xref:System.Windows.Forms.Control.ProcessDialogKey%2A> vb. hiyerarşideki en üstteki denetlemek için üst denetim adı verilir. Bu yöntem döndürürse `true`, ön işleme tamamlandı ve anahtar bir olay değil oluşturulur. Döndürürse `false`, <xref:System.Windows.Forms.Control.KeyDown> olayı oluşur.|  
  
### <a name="preprocessing-for-a-keypress-event"></a>KeyPress olayı için ön işleme  
  
|Eylem|İlgili yöntemi|Notlar|  
|------------|--------------------|-----------|  
|Denetim tarafından işlenmesi gerektiğini normal bir karakterin anahtarıdır denetleyin|<xref:System.Windows.Forms.Control.IsInputChar%2A>|Bu yöntem karakter normal karakter olup olmadığını döndürür `true`, <xref:System.Windows.Forms.Control.KeyPress> olayı oluşturulur ve başka ön işleme gerçekleşir. Aksi takdirde <xref:System.Windows.Forms.Control.ProcessDialogChar%2A> çağrılır.|  
|Karakter (gibi & Tamam düğmesi üzerinde) bir anımsatıcı olup olmadığını denetleyin|<xref:System.Windows.Forms.Control.ProcessDialogChar%2A>|Bu yöntem, benzer <xref:System.Windows.Forms.Control.ProcessDialogKey%2A>, denetim hiyerarşisinde yukarı çağrılır. Denetim bir kapsayıcı denetiminin ise çağırarak için anımsatıcıları denetler <xref:System.Windows.Forms.Control.ProcessMnemonic%2A> kendisi ve onun alt denetimleri. Varsa <xref:System.Windows.Forms.Control.ProcessDialogChar%2A> döndürür `true`, <xref:System.Windows.Forms.Control.KeyPress> olay oluşmaz.|  
  
## <a name="processing-keyboard-messages"></a>Klavye iletilerini işleme  
 Klavye ulaşma iletileri sonra <xref:System.Windows.Forms.Control.WndProc%2A> yöntemi bir form veya denetimi, bir dizi geçersiz kılınabilir yöntemleri tarafından işlenir. Bu yöntemlerin her biri döndüren bir <xref:System.Boolean> klavye ileti işlendikten ve denetim tarafından tüketilen olup olmadığını belirten değer. Yöntemlerden birini döndürürse `true`, ileti işlenmiş değerlendirilir ve bu denetimin temel veya üst daha ayrıntılı işleme için aktarılmaz. Aksi takdirde, ileti ileti kuyruğunda kalır ve başka bir yöntem denetimin temel ya da üst işlenebilir. Aşağıdaki tabloda, klavye iletileri işleme yöntemlerini gösterir.  
  
|Yöntem|Notlar|  
|------------|-----------|  
|<xref:System.Windows.Forms.Control.ProcessKeyMessage%2A>|Bu yöntem tarafından alınan tüm klavye iletileri işleyen <xref:System.Windows.Forms.Control.WndProc%2A> denetiminin yöntemi.|  
|<xref:System.Windows.Forms.Control.ProcessKeyPreview%2A>|Bu yöntem, denetimin üst öğeye klavye iletisi gönderir. Varsa <xref:System.Windows.Forms.Control.ProcessKeyPreview%2A> döndürür `true`, anahtar olay, aksi takdirde oluşturulan <xref:System.Windows.Forms.Control.ProcessKeyEventArgs%2A> olarak adlandırılır.|  
|<xref:System.Windows.Forms.Control.ProcessKeyEventArgs%2A>|Bu yöntem başlatır <xref:System.Windows.Forms.Control.KeyDown>, <xref:System.Windows.Forms.Control.KeyPress>, ve <xref:System.Windows.Forms.Control.KeyUp> uygun şekilde olaylar.|  
  
## <a name="overriding-keyboard-methods"></a>Klavye yöntemleri geçersiz kılma  
 Birçok yöntem bir klavye ileti ön işlemesi yapılan ve işlenen geçersiz kılma için kullanılabilir; Ancak, bazı yöntemler diğerlerinden daha iyi kadar seçimlerdir. Aşağıdaki tabloda gerçekleştirmek isteyebileceğiniz görevler ve klavye yöntemleri geçersiz kılmak için en iyi yolu gösterilmektedir. Geçersiz kılma yöntemleri ile ilgili daha fazla bilgi için bkz: [özellikleri ve yöntemleri geçersiz kılma türetilmiş sınıfları](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md#overriding-properties-and-methods-in-derived-classes).  
  
|Görev|Yöntem|  
|----------|------------|  
|Bir gezinme anahtar kesecek ve yükseltmek bir <xref:System.Windows.Forms.Control.KeyDown> olay. Örneğin, sekme ve Return bir metin kutusunda işlenecek istersiniz.|Geçersiz kılma <xref:System.Windows.Forms.Control.IsInputKey%2A>. **Not:** alternatif olarak, işleyebilir <xref:System.Windows.Forms.Control.PreviewKeyDown> olay ve kümesi <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A> , <xref:System.Windows.Forms.PreviewKeyDownEventArgs> için `true` anahtarı veya istediğiniz anahtarları için.|  
|Özel giriş ya da gezinti işleme bir denetimi gerçekleştirin. Örneğin, seçili öğe değiştirmek için liste denetiminde ok tuşlarını kullanın istiyorsunuz.|geçersiz kılma <xref:System.Windows.Forms.Control.ProcessDialogKey%2A>|  
|Bir gezinme anahtar kesecek ve yükseltmek bir <xref:System.Windows.Forms.Control.KeyPress> olay. Örneğin bir döndürme kutusunu denetiminde öğeler arasında progression hızlandırmak için birden çok ok tuşuna bastığında istiyorsunuz.|Geçersiz kılma <xref:System.Windows.Forms.Control.IsInputChar%2A>.|  
|Özel giriş ya da gezinti işleme sırasında gerçekleştirmek bir <xref:System.Windows.Forms.Control.KeyPress> olay. Örneğin, bir liste r harfle başlayan öğeleri arasında "r" tuşunu basılı tutarak denetimi atlar.|geçersiz kılma <xref:System.Windows.Forms.Control.ProcessDialogChar%2A>|  
|İşleme özel anımsatıcı gerçekleştirir; Örneğin, araç çubuğunda yer alan sahip tarafından çizilmiş düğmeleri anımsatıcıları işlemek istersiniz.|Geçersiz kılma <xref:System.Windows.Forms.Control.ProcessMnemonic%2A>.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Keys>  
 <xref:System.Windows.Forms.Control.WndProc%2A>  
 <xref:System.Windows.Forms.Control.PreProcessMessage%2A>  
 [My.Computer.Keyboard Nesnesi](~/docs/visual-basic/language-reference/objects/my-computer-keyboard-object.md)  
 [Klavyeye Erişme](~/docs/visual-basic/developing-apps/programming/computer-resources/accessing-the-keyboard.md)  
 [Klavye Olaylarını Kullanma](../../../docs/framework/winforms/using-keyboard-events.md)
