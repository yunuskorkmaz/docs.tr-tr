---
title: Bir LINQ to DataSet projesi Visual Studio'da oluşturma
ms.date: 08/15/2018
ms.assetid: 49ba6cb0-cdd2-4571-aeaa-25bf0f40e9b3
ms.openlocfilehash: 22763d3b9581d09d7bdda0c09480f8d36bb8e2ec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667059"
---
# <a name="how-to-create-a-linq-to-dataset-project-in-visual-studio"></a>Nasıl yapılır: Bir LINQ to DataSet projesi Visual Studio'da oluşturma

Belirli bütünleştirilmiş kod başvuruları ve içeri aktarılan ad alanlarını (Visual Basic) LINQ projeleri farklı türde gerektirir veya [kullanarak](../../../csharp/language-reference/keywords/using-directive.md) yönergeleri (C#). LINQ için en düşük gereksinimi başvurusudur *System.Core.dll* ve `using` yönergesi <xref:System.Linq>.

Visual Studio 2017'de yeni bir C# konsol uygulaması projesi oluşturursanız, bu gereksinimleri varsayılan olarak sağlanır. Bir projeyi Visual Studio'nun önceki bir sürümden yükseltiyorsanız, LINQ ile ilgili bu başvuruları el ile sağlamanız gerekebilir.

LINQ to DataSet gerektiren iki ek başvurular *System.Data.dll* ve *System.Data.DataSetExtensions.dll*.

> [!NOTE]
> Bir komut istemi'nden oluşturuyorsanız, el ile LINQ ilgili DLL'leri başvurmalıdır *%ProgramFiles%\Reference Assemblies\Microsoft\Framework\v3.5*.

## <a name="to-enable-linq-to-dataset-functionality"></a>LINQ DataSet işlevselliğini etkinleştirmek için

Varolan bir projede veri kümesi işlevine LINQ'i etkinleştirmek için aşağıdaki adımları izleyin.

1. Başvuruları Ekle **System.Core**, **System.Data**, ve **System.Data.DataSetExtensions**.

   İçinde **Çözüm Gezgini**, sağ **başvuruları** düğümünü seçip alt **Başvuru Ekle**. İçinde **başvuru Yöneticisi** iletişim kutusunda **System.Core**, **System.Data**, ve **System.Data.DataSetExtensions**. **Tamam**’ı seçin.

1. Ekleme [kullanarak](../../../csharp/language-reference/keywords/using-directive.md) yönergeleri (veya [aktarır deyimleri](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) Visual Basic'te) için **System.Data** ve **System.Linq**.

   ```csharp
   using System.Data;
   using System.Linq;
   ```

1. İsteğe bağlı olarak, ekleme bir `using` yönergesi (veya `Imports` deyimi) için **System.Data.Common** veya **System.Data.SqlClient**veritabanına bağlandığınız nasıl bağlı olarak.

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to DataSet kullanmaya başlama](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)
