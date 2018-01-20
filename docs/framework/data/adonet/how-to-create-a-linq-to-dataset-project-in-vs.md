---
title: "Nasıl yapılır: Visual Studio'da bir LINQ to DataSet projesi oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 49ba6cb0-cdd2-4571-aeaa-25bf0f40e9b3
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c749cdd56f0c964b84788b05470406234ef3eb0a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-create-a-linq-to-dataset-project-in-visual-studio"></a>Nasıl yapılır: Visual Studio'da bir LINQ to DataSet projesi oluşturma
Farklı türde [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] projeleri gerektiren belirli içeri aktarılan ad alanları (Visual Basic) veya `using` yönergeleri (C#) ve başvuruları. En düşük gereksinim System.Core.dll başvurusudur ve `using` için yönerge <xref:System.Linq>. Yeni bir oluşturursanız, varsayılan olarak, bunlar sağlanan [!INCLUDE[csharp_orcas_long](../../../../includes/csharp-orcas-long-md.md)] projesi. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]Ayrıca bir başvuru System.Data.dll ve System.Data.DataSetExtensions.dll gerektirir ve bir `Imports` (Visual Basic) veya `using` yönergesi (C#).  
  
 Bir proje Visual Studio'nun önceki bir sürümünden yükseltme yapıyorsanız, bu LINQ ile ilgili başvuruları el ile sağlamanız gerekebilir. .NET Framework sürüm 3.5 hedeflemek için projeyi el ile ayarlamanız gerekebilir.  
  
> [!NOTE]
>  Bir komut isteminden oluşturuluyorsa, el ile LINQ ile ilgili DLL'leri başvurmalıdır `drive` **:**\Program Files\Reference Assemblies\Microsoft\Framework\v3.5.  
  
### <a name="to-target-the-net-framework-35"></a>Hedef .NET Framework 3.5  
  
1.  İçinde [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)], yeni bir Visual Basic veya C# projesi oluşturun. Alternatif olarak, Visual Studio 2005'te oluşturulmuş bir Visual Basic veya C# projesini açın ve dönüştürün yönergeleri izleyerek bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] projesi.  
  
2.  Bir C# projesi için tıklatın **proje** menüsüne ve ardından **özellikleri**.  
  
    1.  İçinde **uygulama** özellik sayfası, select .NET Framework 3.5 **hedef Framework** aşağı açılan liste.  
  
3.  Visual Basic proje için tıklatın **proje** menüsüne ve ardından **özellikleri**.  
  
    1.  İçinde **derleme** özellik sayfası, tıklatın **Gelişmiş derleme seçenekleri** ve .NET Framework 3. 5'ın ardından **hedef Framework'ü (tüm yapılandırmaları)** aşağı açılan liste.  
  
4.  Üzerinde **proje** menüsünde tıklatın **Başvuru Ekle**, tıklatın **.NET** sekmesinde, aşağı kaydırarak **System.Core**, tıklatın ve ardından tıklatın **Tamam**.  
  
5.  Ekleme bir `using` yönergesi veya içeri aktarılan ad alanı için <xref:System.Linq> kaynak kodu dosyasının veya projesi.  
  
     Daha fazla bilgi için bkz: [using yönergesi](~/docs/csharp/language-reference/keywords/using-directive.md) veya [nasıl yapılır: içeri aktarılan ad alanları (Visual Basic) ekleyip](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).  
  
### <a name="to-enable-linq-to-dataset-functionality"></a>LINQ DataSet işlevselliğini etkinleştirmek için  
  
1.  Gerekirse, System.Core.dll başvuru eklemek için bu konunun önceki adımları ve `using` System.Linq için yönerge veya içeri aktarılan ad alanı.  
  
2.  C# veya Visual Basic tıklatın **proje** menüsüne ve ardından **Başvuru Ekle**.  
  
3.  İçinde **Başvuru Ekle** iletişim kutusu, tıklatın **.NET** üstte değilse sekmesinde. Ekranı aşağı kaydırarak **System.Data** ve **System.Data.DataSetExtensions** ve bunlar üzerinde'ı tıklatın. Tıklatın **Tamam** düğmesi.  
  
4.  Ekleme bir `using` yönergesi veya içeri aktarılan ad alanı için <xref:System.Data> kaynak kodu dosyasının veya projesi. Daha fazla bilgi için bkz: [using yönergesi](~/docs/csharp/language-reference/keywords/using-directive.md) veya [nasıl yapılır: içeri aktarılan ad alanları (Visual Basic) ekleyip](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).  
  
5.  System.Data.DataSetExtensions.dll başvuru Dataset işlevselliğini LINQ ekleyin. Zaten yoksa, System.Data.dll bir başvuru ekleyin.  
  
6.  İsteğe bağlı olarak ekleyin bir `using` yönergesi veya içeri aktarılan ad alanı için `System.Data.Common` veya `System.Data.SqlClient`veritabanına nasıl bağlanacağınızı bağlı olarak.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Başlarken](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)  
 [LINQ Kullanmaya Başlama](http://msdn.microsoft.com/library/6cc9af04-950a-4cc3-83d4-2aeb4abe4de9)
