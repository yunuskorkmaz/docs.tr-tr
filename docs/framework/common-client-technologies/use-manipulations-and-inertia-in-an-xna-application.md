---
title: XNA Uygulamasında Düzenlemeleri ve Eylemsizliği Kullanma
ms.date: 03/30/2017
ms.assetid: b7c18905-850c-4da4-8977-a074406a4263
ms.openlocfilehash: 70b8d0c5c098089b6f16ef817ff86698f68cf7c3
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44248910"
---
# <a name="using-manipulations-and-inertia-in-an-xna-application"></a>XNA Uygulamasında Düzenlemeleri ve Eylemsizliği Kullanma
Bu makalede, oyun parçaları hareketini denetlemek için düzenlemeleri ve Eylemsizliği Microsoft XNA uygulamasında işleme nasıl kullanabileceğinizi açıklar. Bu makalede okumadan önce sahibi olmalısınız [düzenlemelere ve Eylemsizliğe genel bakış](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md) konu ve temel XNA ile programlama kavramları hakkında bilgi sahibi olun.  
  
 Bu makalede açıklanan görevler gerçekleştirmek için XNA projenizi başvurmalıdır <xref:System.Windows.Input.Manipulations> derlemede olmalıdır [XNA oyun stüdyosu](https://msdn.microsoft.com/library/bb200104.aspx) ([indirme](https://www.microsoft.com/downloads/details.aspx?FamilyId=7D70D6ED-1EDD-4852-9883-9A33C0AD8FEE&displaylang=en)) bilgisayarınızda yüklü şekilde, Proje XNA derlemelere başvurabilir.  
  
## <a name="overview-of-functionality"></a>İşlevselliğine genel bakış  
 Bu makalede düzenleme ve eylemsizliğe işleme kullanan bir oyun temsil eden özel bir sınıfın nasıl oluşturulacağı gösterilmektedir. Bu sınıf fare ile sürükleyerek ve sonra bırakarak oyun bir ekranda yönetmenize olanak sağlar. Yayımlanan sonra tutar işleme için Eylemsizliği olarak kademeli olarak taşıma oyun parça yavaşlar. Taşıma doğrusal ve angular ' dir.  
  
 ![Basit düzenlemeler ve eylemsizlik uygulama. ](../../../docs/framework/common-client-technologies/media/ndp-gamexna.jpg "NDP_GameXna")  
  
 Ayrıca, özel bir koleksiyona birden fazla oyun parçaları yöneten oluşturulur. Bu XNA oyununun sınıfından gerekli işleme kolaylaştırır.  
  
 [GamePiece Sınıfı Oluşturma](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md)  
  
 [GamePieceCollection Sınıfı Oluşturma](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)  
  
 [Game1 Sınıfı Oluşturma](../../../docs/framework/common-client-technologies/creating-the-game1-class.md)  
  
 [Tam Kod Listeleri](../../../docs/framework/common-client-technologies/full-code-listings.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Input.Manipulations>  
 [Düzenlemelere ve Eylemsizliğe Genel Bakış](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md)
