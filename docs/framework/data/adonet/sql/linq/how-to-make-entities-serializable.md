---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: varlıkları seri hale getirme'
title: 'Nasıl yapılır: Varlıkları Serileştirilebilir Hale Getirme'
ms.date: 03/30/2017
ms.assetid: a6c5bf6e-064a-4f77-b74c-76b3a5dec309
ms.openlocfilehash: cb2253d7933f3584543b4b030bc8b5aa3cc62921
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785945"
---
# <a name="how-to-make-entities-serializable"></a><span data-ttu-id="87a1e-103">Nasıl yapılır: Varlıkları Serileştirilebilir Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="87a1e-103">How to: Make Entities Serializable</span></span>

<span data-ttu-id="87a1e-104">Kodunuzu oluştururken varlıkları seri hale getirilebilir hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87a1e-104">You can make entities serializable when you generate your code.</span></span> <span data-ttu-id="87a1e-105">Varlık sınıfları özniteliğiyle <xref:System.Runtime.Serialization.DataContractAttribute> ve özniteliğiyle birlikte sütunlar halinde tasarlanmalıdır <xref:System.Runtime.Serialization.DataMemberAttribute> .</span><span class="sxs-lookup"><span data-stu-id="87a1e-105">Entity classes are decorated with the <xref:System.Runtime.Serialization.DataContractAttribute> attribute, and columns with the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute.</span></span>  
  
 <span data-ttu-id="87a1e-106">Visual Studio kullanan geliştiriciler bu amaçla Nesne İlişkisel Tasarımcısı kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="87a1e-106">Developers using Visual Studio can use the Object Relational Designer for this purpose.</span></span>  
  
 <span data-ttu-id="87a1e-107">SQLMetal komut satırı aracını kullanıyorsanız, **/Serialization** seçeneğini `unidirectional` bağımsız değişkeniyle birlikte kullanın.</span><span class="sxs-lookup"><span data-stu-id="87a1e-107">If you are using the SQLMetal command-line tool, use the **/serialization** option with the `unidirectional` argument.</span></span> <span data-ttu-id="87a1e-108">Daha fazla bilgi için bkz. [SqlMetal.exe (kod üretme aracı)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="87a1e-108">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="87a1e-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="87a1e-109">Example</span></span>  

 <span data-ttu-id="87a1e-110">Aşağıdaki SQLMetal komut satırları, serileştirilebilir varlıkları olan dosyaları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="87a1e-110">The following SQLMetal command lines produce files that have serializable entities.</span></span>  
  
```console  
sqlmetal /code:nwserializable.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
```console  
sqlmetal /code:nwserializable.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
## <a name="see-also"></a><span data-ttu-id="87a1e-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="87a1e-111">See also</span></span>

- [<span data-ttu-id="87a1e-112">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="87a1e-112">Serialization</span></span>](serialization.md)
- [<span data-ttu-id="87a1e-113">Nesne Modeli Oluşturma</span><span class="sxs-lookup"><span data-stu-id="87a1e-113">Creating the Object Model</span></span>](creating-the-object-model.md)
