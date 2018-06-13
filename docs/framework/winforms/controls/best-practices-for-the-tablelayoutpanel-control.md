---
title: TableLayoutPanel Denetimi için En İyi Yöntemler
ms.date: 03/30/2017
helpviewer_keywords:
- layout [Windows Forms]
- TableLayoutPanel control [Windows Forms], best practices
- forms [Windows Forms], best practices
- AutoSize property [Windows Forms], tableLayoutPanel control
- controls [Windows Forms], sizing
- TableLayoutPanel control [Windows Forms], AutoSize behavior
- layout [Windows Forms], AutoSize
- layout [Windows Forms], best practices
- best practices [Windows Forms], tableLayoutPanel control
- sizing [Windows Forms], automatic
- automatic sizing
ms.assetid: b6706efb-d7a4-45ec-8cf4-08fa993e3afb
ms.openlocfilehash: 40322dc6c5facd4167a4c9ac5c12fdf2a8831b7c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526459"
---
# <a name="best-practices-for-the-tablelayoutpanel-control"></a>TableLayoutPanel Denetimi için En İyi Yöntemler
<xref:System.Windows.Forms.TableLayoutPanel> Denetim dikkatle Windows formlarında kullanmadan önce dikkate almanız gereken güçlü yerleşim özellikleri sağlar.  
  
## <a name="recommendations"></a>Önerileri  
 Aşağıdaki öneriler kullanmanıza yardımcı <xref:System.Windows.Forms.TableLayoutPanel> en iyi kendi yararınıza denetim.  
  
### <a name="targeted-use"></a>Hedeflenen kullanın  
 Kullanım <xref:System.Windows.Forms.TableLayoutPanel> tutumlu denetim. Onu yeniden boyutlandırılabilir düzeni gerektiren tüm durumlarda kullanmamanız gerekir. Aşağıdaki listede kullanımı en fazla yararlanır düzenleri açıklanmaktadır <xref:System.Windows.Forms.TableLayoutPanel> denetimi:  
  
-   Formun orantılı olarak birbirlerine yeniden boyutlandırmak birden çok bölümleri olan düzenler.  
  
-   Değiştirilen veya eklenir veya çıkarılır kullanıcı özelleştirilebilir alanlar veri girişi formları gibi çalışma zamanında dinamik olarak üretilen düzenleri tercihlerinize göre temel.  
  
-   Genel sabit boyutta kalacağı düzenler. Örneğin, 800 x 600'den küçük kalması gereken bir iletişim kutusu olabilir, ancak yerelleştirilmiş dizeleri desteklemesi gerekir.  
  
 Aşağıdaki listede kullanımından büyük ölçüde faydalanmaz düzenleri açıklanmaktadır <xref:System.Windows.Forms.TableLayoutPanel> denetimi:  
  
-   Basit veri girişi formlarla tek bir sütun etiketleri ve metin girişi alanlarının tek bir sütun.  
  
-   Tek bir büyük formlarla bir yeniden boyutlandırma meydana geldiğinde, tüm kullanılabilir alanı dolduracak alanı görüntüler. Bu, tek bir görüntüleyen bir form örneğidir <xref:System.Windows.Forms.PropertyGrid> denetim. Bu durumda, formu yeniden boyutlandırıldığında hiçbir şey genişletmeniz gerekir çünkü sabitleme, kullanın.  
  
 Hangi denetimlerin olması gereken seçerken dikkatli bir <xref:System.Windows.Forms.TableLayoutPanel> denetim. %30 sabitleme kullanarak tarafından büyümeye metninizi yer varsa, kullanmayı <xref:System.Windows.Forms.Control.Anchor%2A> yalnızca özelliği. Düzeninizi tarafından gerekli alanı tahmin edebilirsiniz, kullanımı <xref:System.Windows.Forms.Control.Dock%2A> ve <xref:System.Windows.Forms.Control.Anchor%2A> kalan alanın ayrıntılarını tahmin daha kolaydır ve <xref:System.Windows.Forms.Control.AutoSize%2A> davranışı.  
  
 Genel olarak, düzeniyle tasarlarken, <xref:System.Windows.Forms.TableLayoutPanel> denetlemek, tasarım olabildiğince basit tutun.  
  
### <a name="use-the-document-outline-window"></a>Belge Anahattı penceresi kullanın  
 Belge Anahattı penceresi denetimlerinizi z düzeni ve üst-alt ilişkilerini yönetmek için kullanabileceğiniz düzeninizi ağaç görünümünü sağlar. Gelen **Görünüm menüsünde**seçin **diğer pencereler**seçeneğini belirleyip **belge anahattı**.  
  
### <a name="avoid-nesting"></a>İç içe geçme kaçının  
 İç içe geçme diğer kaçının <xref:System.Windows.Forms.TableLayoutPanel> içinde denetleyen bir <xref:System.Windows.Forms.TableLayoutPanel> denetim. İç içe geçmiş düzenleri hata ayıklama zor olabilir.  
  
### <a name="avoid-visual-inheritance"></a>Görsel devralma kaçının  
 <xref:System.Windows.Forms.TableLayoutPanel> Denetimi Windows Forms Tasarımcısı'nda görsel devralma desteklemez. A <xref:System.Windows.Forms.TableLayoutPanel> türetilmiş bir sınıf denetiminde "tasarım zamanında kilitli"olarak görüntülenir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 <xref:System.Windows.Forms.FlowLayoutPanel>
