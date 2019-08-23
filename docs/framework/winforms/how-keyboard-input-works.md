---
title: Klavye Girdisi Nasıl Çalışır
ms.date: 03/30/2017
helpviewer_keywords:
- keyboard input [Windows Forms], about keyboard input
- keyboards [Windows Forms], keyboard input
- Windows Forms, keyboard input
ms.assetid: 9a29433c-a180-49bb-b74c-d187786584c8
ms.openlocfilehash: 369c434f5443334ccb8b136ce50ff2d5db8ece01
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963441"
---
# <a name="how-keyboard-input-works"></a>Klavye Girdisi Nasıl Çalışır
Windows Forms, Windows iletilerine yanıt olarak klavye olaylarını yükselterek klavye girişini işler. Çoğu Windows Forms uygulama klavye olaylarını işleyerek klavye girişini yalnızca işler. Ancak klavye iletilerinin nasıl çalıştığını anlamanız gerekir. böylece, bir denetime erişmeden önce anahtarları kesintiye uğratan önce, daha gelişmiş klavye girişi senaryolarına de uygulayabilirsiniz. Bu konu, Windows Forms tanıdığı anahtar verisi türlerini açıklar ve klavye iletilerinin nasıl yönlendirildiğini gösteren bir genel bakış sağlar. Klavye olayları hakkında daha fazla bilgi için bkz. [klavye olaylarını kullanma](using-keyboard-events.md).  
  
## <a name="types-of-keys"></a>Anahtar türleri  
 Windows Forms, klavye girişini bit düzeyinde <xref:System.Windows.Forms.Keys> numaralandırma tarafından temsil edilen sanal anahtar kodları olarak tanımlar. <xref:System.Windows.Forms.Keys> Numaralandırmada, bir dizi basılan tuşu birleştirerek tek bir değer elde edebilirsiniz. Bu değerler, WM_KEYDOWN ve WM_SYSKEYDOWN Windows iletilerine eşlik eden değerlere karşılık gelir. <xref:System.Windows.Forms.Control.KeyDown> Veya<xref:System.Windows.Forms.Control.KeyUp> olaylarını işleyerek fiziksel anahtar basışlarını tespit edebilirsiniz. Karakter anahtarları, <xref:System.Windows.Forms.Keys> numaralandırmanın bir alt kümesidir ve WM_CHAR ve wm_syschar Windows iletilerine eşlik eden değerlere karşılık gelir. Basılan anahtarların birleşimi bir karakter ile sonuçlanırsa, <xref:System.Windows.Forms.Control.KeyPress> olayı işleyerek karakteri tespit edebilirsiniz. Alternatif olarak, hangi anahtarların <xref:Microsoft.VisualBasic.Devices.Keyboard>basılan ve hangi anahtarlara gönderileceğini öğrenmek için Visual Basic programlama arabirimi tarafından açığa çıkarılan ' i kullanabilirsiniz. Daha fazla bilgi için bkz. [klavyeye erişme](../../visual-basic/developing-apps/programming/computer-resources/accessing-the-keyboard.md).  
  
## <a name="order-of-keyboard-events"></a>Klavye olaylarının sırası  
 Daha önce listelendiğinde, bir denetimde gerçekleşebileceğini 3 klavye ile ilgili olaylar vardır. Aşağıdaki sırada olayların genel sırası gösterilmektedir:  
  
1. Kullanıcı "a" anahtarını iter, anahtar önceden işlenir, gönderilir ve bir <xref:System.Windows.Forms.Control.KeyDown> olay oluşur.  
  
2. Kullanıcı, "a" anahtarını barındırır, anahtar önceden işlenir, gönderilir ve bir <xref:System.Windows.Forms.Control.KeyPress> olay oluşur.  
  
     Bu olay, Kullanıcı bir anahtar taşıdığı için birden çok kez meydana gelir.  
  
3. Kullanıcı, "a" anahtarını yayınlar, anahtar önceden işlenir, gönderilir ve bir <xref:System.Windows.Forms.Control.KeyUp> olay oluşur.  
  
## <a name="preprocessing-keys"></a>Ön işleme anahtarları  
 Diğer iletiler gibi, klavye iletileri bir form veya denetim <xref:System.Windows.Forms.Control.WndProc%2A> yönteminde işlenir. Ancak, klavye iletileri işlenmeden önce, <xref:System.Windows.Forms.Control.PreProcessMessage%2A> yöntemi özel karakter anahtarlarını ve fiziksel anahtarları işlemek için geçersiz kılınabilen bir veya daha fazla yöntemi çağırır. İletiler denetim tarafından işlenmeden önce belirli anahtarları algılamak ve filtrelemek için bu yöntemleri geçersiz kılabilirsiniz. Aşağıdaki tabloda, gerçekleştirilen eylem ve yöntemin gerçekleştiği sırada gerçekleşen ilgili yöntem gösterilmektedir.  
  
### <a name="preprocessing-for-a-keydown-event"></a>KeyDown olayı için ön işleme  
  
|Eylem|İlgili Yöntem|Notlar|  
|------------|--------------------|-----------|  
|Hızlandırıcı veya Menü kısayolu gibi bir komut anahtarını kontrol edin.|<xref:System.Windows.Forms.Control.ProcessCmdKey%2A>|Bu yöntem, normal anahtarlardan daha fazla önceliğe sahip bir komut anahtarını işler. Bu yöntem `true`döndürülürse, anahtar ileti gönderilir ve bir anahtar olay oluşmaz. Döndürürse `false`, <xref:System.Windows.Forms.Control.IsInputKey%2A> çağırılır`.`|  
|Bir <xref:System.Windows.Forms.Control.KeyDown> olayı oluşturması ve bir denetime dağıtılması gereken, ön işleme veya normal bir karakter anahtarı gerektiren özel bir anahtar olup olmadığını denetleyin.|<xref:System.Windows.Forms.Control.IsInputKey%2A>|Yöntemi döndürürse `true`, denetimin normal bir karakter ve bir <xref:System.Windows.Forms.Control.KeyDown> olay tetiklenir demektir. İse `false`çağırılır. <xref:System.Windows.Forms.Control.ProcessDialogKey%2A> **Not:**  Bir denetimin anahtar veya anahtarların birleşimini aldığından <xref:System.Windows.Forms.Control.PreviewKeyDown> emin olmak için, olay ve kümesini <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A> <xref:System.Windows.Forms.PreviewKeyDownEventArgs> istediğiniz anahtar veya anahtarlar için olarak `true` işleyebilirsiniz.|  
|Bir gezinti anahtarı (ESC, sekme, dönüş veya ok tuşları) olup olmadığını denetleyin.|<xref:System.Windows.Forms.Control.ProcessDialogKey%2A>|Bu yöntem, denetimin içindeki özel işlevleri kullanan bir fiziksel anahtarı işler, örneğin denetim ve üstü arasındaki odağı değiştirme. Acil denetim anahtarı <xref:System.Windows.Forms.Control.ProcessDialogKey%2A> işlemezse, üst denetimde ve bu şekilde hiyerarşide en üstteki denetime çağrılır. Bu yöntem `true`döndürülürse, ön işleme tamamlanmıştır ve bir anahtar olay oluşturulmaz. Döndürürse `false` bir<xref:System.Windows.Forms.Control.KeyDown> olay oluşur.|  
  
### <a name="preprocessing-for-a-keypress-event"></a>KeyPress olayı için ön işleme  
  
|Eylem|İlgili Yöntem|Notlar|  
|------------|--------------------|-----------|  
|Anahtarın denetim tarafından işlenmesi gereken normal bir karakter olup olmadığını denetleyin|<xref:System.Windows.Forms.Control.IsInputChar%2A>|Karakter normal bir karakter ise, bu yöntem döndürülür `true` <xref:System.Windows.Forms.Control.KeyPress> , olay tetiklenir ve başka bir ön işleme gerçekleşmez. Aksi <xref:System.Windows.Forms.Control.ProcessDialogChar%2A> takdirde çağrılacaktır.|  
|Karakterin bir anımsatıcı olup olmadığını denetleyin (örneğin, bir düğme üzerinde & Tamam)|<xref:System.Windows.Forms.Control.ProcessDialogChar%2A>|Buna benzer <xref:System.Windows.Forms.Control.ProcessDialogKey%2A>olan bu yöntem, denetim hiyerarşisinin çağrılacaktır. Denetim bir kapsayıcı denetimidir, kendisini ve onun alt denetimlerini çağırarak <xref:System.Windows.Forms.Control.ProcessMnemonic%2A> anımsatıcıları denetler. <xref:System.Windows.Forms.Control.ProcessDialogChar%2A> Dönerse`true`bir olay<xref:System.Windows.Forms.Control.KeyPress> oluşmaz.|  
  
## <a name="processing-keyboard-messages"></a>Klavye Iletilerini işleme  
 Klavye iletileri bir form veya <xref:System.Windows.Forms.Control.WndProc%2A> denetim yöntemine ulaştığında, bunlar geçersiz kılınabilen bir dizi yöntem tarafından işlenir. Bu yöntemlerin her biri, klavye <xref:System.Boolean> mesajının denetim tarafından işlenip tüketilmediğini belirten bir değer döndürür. Yöntemlerin `true`biri döndürülürse, ileti işlenmiş olarak kabul edilir ve daha fazla işleme için denetimin tabanına veya üst öğesine geçirilmez. Aksi takdirde ileti ileti kuyruğunda kalır ve denetimin tabanında veya üst kısmında başka bir yöntemde işlenebilir. Aşağıdaki tabloda, klavye iletilerini işleyen yöntemler sunulmaktadır.  
  
|Yöntem|Notlar|  
|------------|-----------|  
|<xref:System.Windows.Forms.Control.ProcessKeyMessage%2A>|Bu yöntem, denetimin <xref:System.Windows.Forms.Control.WndProc%2A> yöntemi tarafından alınan tüm klavye iletilerini işler.|  
|<xref:System.Windows.Forms.Control.ProcessKeyPreview%2A>|Bu yöntem, klavye iletisini denetimin üst öğesine gönderir. Döndürülürse, hiçbir anahtar olay oluşturulmaz, aksi takdirde <xref:System.Windows.Forms.Control.ProcessKeyEventArgs%2A> çağrılır. `true` <xref:System.Windows.Forms.Control.ProcessKeyPreview%2A>|  
|<xref:System.Windows.Forms.Control.ProcessKeyEventArgs%2A>|Bu yöntem,, <xref:System.Windows.Forms.Control.KeyDown>ve <xref:System.Windows.Forms.Control.KeyPress> <xref:System.Windows.Forms.Control.KeyUp> olaylarını uygun şekilde oluşturur.|  
  
## <a name="overriding-keyboard-methods"></a>Klavye yöntemlerini geçersiz kılma  
 Bir klavye iletisi önceden işlendiğinde ve işlendiğinde geçersiz kılmak için kullanabileceğiniz birçok yöntem vardır; Ancak bazı yöntemler diğerlerinden çok daha iyi seçimlerdir. Aşağıdaki tabloda, gerçekleştirmek isteyebileceğiniz görevler ve klavye yöntemlerini geçersiz kılmanın en iyi yolu gösterilmektedir. Yöntemleri geçersiz kılma hakkında daha fazla bilgi için bkz. [türetilmiş sınıflarda özellikleri ve yöntemleri geçersiz kılma](../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md#overriding-properties-and-methods-in-derived-classes).  
  
|Görev|Yöntem|  
|----------|------------|  
|Bir gezinti anahtarını durdurur ve bir <xref:System.Windows.Forms.Control.KeyDown> olay yükseltin. Örneğin, sekme ve sonra bir metin kutusunda işlenecek şekilde geri dönmek istiyorsunuz.|Geçersiz <xref:System.Windows.Forms.Control.IsInputKey%2A>kıl. **Not:**  Alternatif olarak, istediğiniz anahtar veya <xref:System.Windows.Forms.Control.PreviewKeyDown> anahtarlar `true` için ' <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A> i ve <xref:System.Windows.Forms.PreviewKeyDownEventArgs> ' ı ' a yönelik olay ve kümesini işleyebilirsiniz.|  
|Bir denetimde özel giriş veya gezinme işlemi gerçekleştirin. Örneğin, seçili öğeyi değiştirmek için liste denetiinizdeki ok tuşlarının kullanımını istiyorsunuz.|Manızı<xref:System.Windows.Forms.Control.ProcessDialogKey%2A>|  
|Bir gezinti anahtarını durdurur ve bir <xref:System.Windows.Forms.Control.KeyPress> olay yükseltin. Örneğin, bir döndürme kutusu denetiminde, öğelerin ilerlemesini hızlandırmak için birden fazla ok tuşuna basmayı tercih edebilirsiniz.|Geçersiz <xref:System.Windows.Forms.Control.IsInputChar%2A>kıl.|  
|Bir <xref:System.Windows.Forms.Control.KeyPress> olay sırasında özel giriş veya gezinme işlemi gerçekleştirin. Örneğin, "r" tuşunu basılı tutan liste denetiminde r harfiyle başlayan öğeler arasında atlar.|Manızı<xref:System.Windows.Forms.Control.ProcessDialogChar%2A>|  
|Özel anımsatıcı işleme gerçekleştirin; Örneğin, bir araç çubuğunda bulunan, sahip tarafından çizilen düğmelerde anımsatıcıları işlemek istiyorsunuz.|Geçersiz <xref:System.Windows.Forms.Control.ProcessMnemonic%2A>kıl.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Keys>
- <xref:System.Windows.Forms.Control.WndProc%2A>
- <xref:System.Windows.Forms.Control.PreProcessMessage%2A>
- [My.Computer.Keyboard Nesnesi](../../visual-basic/language-reference/objects/my-computer-keyboard-object.md)
- [Klavyeye Erişme](../../visual-basic/developing-apps/programming/computer-resources/accessing-the-keyboard.md)
- [Klavye Olaylarını Kullanma](using-keyboard-events.md)
