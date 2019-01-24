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
ms.openlocfilehash: 6be6d0904d5b52e5188f0a5a16aaefa08265379c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54674199"
---
# <a name="best-practices-for-the-tablelayoutpanel-control"></a>TableLayoutPanel Denetimi için En İyi Yöntemler
<xref:System.Windows.Forms.TableLayoutPanel> Denetim dikkatli bir şekilde Windows formlarınızı kullanmadan önce dikkate almanız gereken güçlü düzen özelliklerini sağlar.  
  
## <a name="recommendations"></a>Öneriler  
 Aşağıdaki öneriler kullanmanıza yardımcı olacak <xref:System.Windows.Forms.TableLayoutPanel> en iyi avantajı denetimi.  
  
### <a name="targeted-use"></a>Hedeflenen kullanın  
 Kullanım <xref:System.Windows.Forms.TableLayoutPanel> olabildiğince az denetim. Bunu yeniden boyutlandırılabilir düzeni gerektiren tüm durumlarda kullanmamalısınız. Aşağıdaki listede açıklanmıştır kullanımını en iyi yararlanan düzenleri <xref:System.Windows.Forms.TableLayoutPanel> denetimi:  
  
-   Birbirleriyle orantılı olarak yeniden boyutlandırmak birden çok form parçası olan düzenler.  
  
-   Değiştirildiğinde veya eklendiğinde veya çıkarıldığında kullanıcı tarafından özelleştirilebilir alanlara sahip veri girişi formları gibi çalışma zamanında dinamik olarak oluşturulan düzenleri tercihleri temelinde.  
  
-   Genel bir sabit boyutta kalması gereken düzenler. Örneğin, 800 x 600 ' küçük kalması gereken bir iletişim kutusu olabilir, ancak yerelleştirilmiş dizeleri desteklemeniz gerekiyor.  
  
 Aşağıdaki liste önemli ölçüde kullanarak avantaj elde değil düzenleri açıklar <xref:System.Windows.Forms.TableLayoutPanel> denetimi:  
  
-   Etiket ve metin girişi alanlarının tek bir sütun basit veri girişi formları ile tek bir sütun.  
  
-   Bir yeniden boyutlandırma meydana geldiğinde, tüm kullanılabilir alanı dolduracak alan büyük tek bir form görüntüler. Bu, tek bir görüntüleyen bir form örneğidir <xref:System.Windows.Forms.PropertyGrid> denetimi. Formu yeniden boyutlandırıldığında başka bir şey genişletmeniz gerekir çünkü bu durumda, sabitleme, kullanın.  
  
 Hangi denetimlerin olması gereken seçerken dikkatli bir <xref:System.Windows.Forms.TableLayoutPanel> denetimi. Bağlama kullanarak 30 oranında büyümesine metni yer varsa kullanmayı <xref:System.Windows.Forms.Control.Anchor%2A> yalnızca özellik. Düzeninizi tarafından gerekli alanı tahmin edebilirsiniz, kullanım <xref:System.Windows.Forms.Control.Dock%2A> ve <xref:System.Windows.Forms.Control.Anchor%2A> kalan alanı ayrıntılarını tahmin etmek daha kolaydır ve <xref:System.Windows.Forms.Control.AutoSize%2A> davranışı.  
  
 Genel olarak ile düzeninizi tasarlarken, <xref:System.Windows.Forms.TableLayoutPanel> denetlemek, tasarım, olabildiğince basit tutun.  
  
### <a name="use-the-document-outline-window"></a>Belge Anahattı penceresini kullanma  
 Belge Anahattı penceresi denetimlerinizi z düzenini ve üst-alt ilişkilerini yönetmek için kullanabileceğiniz düzeninizi ağaç görünümünü sağlar. Gelen **Görünüm menüsü**seçin **diğer Windows**, ardından **belge anahattı**.  
  
### <a name="avoid-nesting"></a>İç içe geçme kaçının  
 İç içe diğer önlemek <xref:System.Windows.Forms.TableLayoutPanel> içinde denetleyen bir <xref:System.Windows.Forms.TableLayoutPanel> denetimi. İç içe geçmiş düzenleri hata ayıklaması zor olabilir.  
  
### <a name="avoid-visual-inheritance"></a>Görsel devralmadan kaçının  
 <xref:System.Windows.Forms.TableLayoutPanel> Denetimi Windows Form Tasarımcısı'nda görsel devralmayı desteklemez. A <xref:System.Windows.Forms.TableLayoutPanel> "tasarım zamanında kilitli gibi" Denetim türetilmiş bir sınıf içinde görünür.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>
